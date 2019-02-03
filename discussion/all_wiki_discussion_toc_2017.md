[2017-01-27 01:43:21 - pterminator - Random order Keywords and pyparsing operator order](.#2017-01-27-014321---pterminator---random-order-keywords-and-pyparsing-operator-order)  
[2017-01-27 10:08:29 - lhughes42 - White Space and LineStart](.#2017-01-27-100829---lhughes42---white-space-and-linestart)  
[2017-02-02 15:54:25 - Justin-Fay - Fantastic little library](.#2017-02-02-155425---justin-fay---fantastic-little-library)  
[2017-02-04 17:24:41 - AngshumanGuha - there's a bug in fnumber](.#2017-02-04-172441---angshumanguha---theres-a-bug-in-fnumber)  
[2017-02-08 06:43:53 - cdeluna - Multiline Expression](.#2017-02-08-064353---cdeluna---multiline-expression)  
[2017-03-23 19:47:43 - borismarin - Issues with {{oc.py}} example](.#2017-03-23-194743---borismarin---issues-with-{{ocpy}}-example)  
[2017-04-07 01:14:46 - Lucas-C - Parsing mardown-styled text](.#2017-04-07-011446---lucas-c---parsing-mardown-styled-text)  
[2017-04-14 02:06:52 - pterminator - SkipTo combined with CaselessKeyword gives unexpected results (possible bug)](.#2017-04-14-020652---pterminator---skipto-combined-with-caselesskeyword-gives-unexpected-results-possible-bug)  
[2017-05-30 11:39:49 - qrun - Formal-Tranlastion](.#2017-05-30-113949---qrun---formal-tranlastion)  
[2017-06-26 16:35:01 - EvanHub - Prevent an element from matching dependent on context](.#2017-06-26-163501---evanhub---prevent-an-element-from-matching-dependent-on-context)  
[2017-08-03 10:43:07 - ferenc0521 - Group result question](.#2017-08-03-104307---ferenc0521---group-result-question)  
[2017-08-13 16:19:26 - ferenc0521 - schemaSQL.parseFile(f) fails if parseAll=True attemted](.#2017-08-13-161926---ferenc0521---schemasqlparsefilef-fails-if-parsealltrue-attemted)  
[2017-08-16 08:12:45 - mdemi - Odd .copy() behaviour](.#2017-08-16-081245---mdemi---odd-copy-behaviour)  
[2017-08-27 19:25:52 - vacaut - += operator and user function for math equation](.#2017-08-27-192552---vacaut----operator-and-user-function-for-math-equation)  


---
## 2017-01-27 01:43:21 - pterminator - Random order Keywords and pyparsing operator order
Hi, 

I'm trying to write a parser for text files that contain keywords in random order, this is why I'm using Each(). Now I'm facing a problem the problem that the the pyparsing expressions don't seem distributive i.e. A & (B ^ C) != (A & B) ^ (A & C). 
The code below demonstrates the problem more clearly. What would be a proper solution in this case? Is there a way to force pyparsing to expand the expressions?

Any help is much appreciated.



    from pyparsing import *
    
    text = '''
    MANDATORY ALT_ONE ALT_ONE_OPT 
    '''
    
    mandatory = Keyword('MANDATORY')
    alt_one =  Keyword('ALT_ONE') & Optional(Keyword('ALT_ONE_OPT'))
    alt_two =  Keyword('ALT_TWO') & Optional(Keyword('ALT_TWO_OPT'))
    
    expr_each_first = (mandatory & alt_one) ^ (mandatory & alt_two) 
    expr_or_first = mandatory & (alt_one ^ alt_two)
    
    res_each_first= expr_each_first.parseString(text)
    res_or_first = expr_or_first.parseString(text)
    
    # no problems here
    print res_each_first.asList()   == ['MANDATORY', 'ALT_ONE', 'ALT_ONE_OPT'] # True
    print res_or_first.asList()     == ['MANDATORY', 'ALT_ONE', 'ALT_ONE_OPT'] # True
    
    # order modified
    text = '''
    ALT_ONE MANDATORY ALT_ONE_OPT 
    '''
    
    res_each_first= expr_each_first.parseString(text)
    res_or_first = expr_or_first.parseString(text)
    
    print res_each_first.asList()   == ['ALT_ONE', 'MANDATORY', 'ALT_ONE_OPT'] # True
    print res_or_first.asList()     == ['ALT_ONE', 'MANDATORY', 'ALT_ONE_OPT'] # False result is ['ALT_ONE', 'MANDATORY']



#### 2017-01-28 09:00:10 - ptmcg
This may be one of the downsides to the basic concept of operator overloading: people assume that operators will work with your code like they do in arithmetic. But pyparsing already violates some of these arithmetic models: exprA + exprB is clearly not equivalent to exprB + exprA. So we need to bear in mind the way these operators are being applied, beyond just their common arithmetic sensibilities (we *do* have to maintain precedence of operations, since that is done by the Python interpreter itself, and cannot be overridden). In your example, A & (B ^ C), where B and C are both Each expressions, the Each expression with A does not peer inside the contents of the Or term to do additional Each'ing with the terms in it. Now pyparsing *does* do some manipulation of terms in its streamline() processing (combining like operations like '(A | B) | C' to 'A | B | C'). So there may be a possibility to have streamline do some of the kind of expansion/distributivity that you describe. But that will have to wait for a future release.  In the mean time, I think you will have to do your own Each combinations. Thanks for the idea, I'll have to try some experiments with it.
#### 2017-01-30 01:52:18 - pterminator
Thanks for your answer, I understand that it could only could work for Each and Or since order matters, but in a case like this, such an option would be great. 
Of course the example above is reduced to the bare minimum and rewriting the expression is trivial. The actual parser I've written is based on a rather extensive five page BNF specification (in which order does not matter) with many 'exclusive or' statements that could be nested as well. That would make expanding the terms nearly impossible if not done automatically.
A workaround could be to be less strict with the grammar and resort to ZeroOrMore(A | B | C | D | E | ....)  where A to E represent 'single' expressions, i.e. in the example 'alt_one' would be split in two parts and one can drop 'Optional()'. The only downside would be that the parser will not be able to detect missing mandatory fields, but that could be left for a post-parsing operation.
#### 2017-01-30 06:53:00 - ptmcg
A parse action would be a decent compromise for now. I'll revisit my current operations with an eye to which ones should be commutative and associative, and see if I can get streamline() to do more of this heavy lifting. With this change, I'll probably release as v2.2.0.

---
## 2017-01-27 10:08:29 - lhughes42 - White Space and LineStart
First, great tool! Second, I am confused as to why lineStart fails to match if the line starts with some white space. So for example if my pattern is:
patt = lineStart + 'foo'
and my test string is:
'foo'
All is good. But if instead my string is ' foo' . It fails.
I thought whitespace was ignored by default. What am I doing wrong please? My goal is to ignore such line starting whitespace.

#### 2017-01-27 10:11:19 - lhughes42
(I do need to retain the startLine also. Can't just drop).
#### 2017-01-27 22:20:41 - ptmcg
Glad to hear you are enjoying working with pyparsing!

LineStart has a checkered past, and the behavior you are requesting was the source of a lot of confusion. Since one of the default whitespace characters is '\n', when LineStart was written to skip over whitespace, it would also skip over newlines, so you could get a match on LineStart *before* the previous LineEnd! I've nailed down LineStart now to match *only* at column 1, regardless of whitespace. If you need to accept whitespace, then try including an Empty() or Optional(White) after LineStart in your grammar:


    patt = lineStart + empty + 'foo'


#### 2017-01-28 16:14:24 - lhughes42
Thanks for your prompt reply. Glad I asked. Don't think I would have gotten there. I had been trying out similar things with 'White' but no success. Had missed 'empty' (or doing Optional(White))
#### 2017-02-07 08:36:16 - lhughes42
Sadly I am being dense. I tried both your approaches and do to misinterpreting (I suspect) they both fail. Here is my test string:
simple_str = ' foo'
here is first approach:
patt = lineStart + Optional(White) + 'foo'
I get a crash using patt.searchSTring(simple_str)
'type object 'White' has no attribute 'mayIndexError'
Then tried alternative pattern:
patt = lineStart + empty + 'foo'
I get no match (returns '[]')
:-(
Please advise this simpleton :-)
#### 2017-02-07 08:36:51 - lhughes42
(note the lead whitespace in ' foo')

---
## 2017-02-02 15:54:25 - Justin-Fay - Fantastic little library
Many thanks for this great software. I recently had a problem where I had a language specific data structure stored as a string in a database. pyparsing made the task very simple to parse this to a python data structure. The source code is also very readable and easy to grok.

#### 2017-02-02 16:36:55 - ptmcg
Glad you found us, and that pyparsing helped you through your problem!
#### 2017-02-03 03:21:11 - Justin-Fay
One little thing I am having a bit of trouble understanding is the `asDict` method is coercing integer keys to strings. I will try to explain with a brief example:

```
<ul class="quotelist"><ul class="quotelist"><ul class="quotelist"><li>from pyparsing import *</li><li>SEP = Suppress(':')</li><li>
</li><li>array = Forward()</li><li>value = Forward()</li><li>
</li><li>value \<\< (pyparsing_common.number() | sglQuotedString().setParseAction(removeQuotes))</li></ul></ul></ul>Forward: ...
<ul class="quotelist"><ul class="quotelist"><ul class="quotelist"><li>array \<\< Dict(delimitedList(Group(value + SEP + value)))</li></ul></ul></ul>Forward: ...
<ul class="quotelist"><ul class="quotelist"><ul class="quotelist"><li>
</li><li>array.parseString('0:0, '1':'1'').asDict()</li></ul></ul></ul>{'1': '1', '0': 0}
<ul class="quotelist"><ul class="quotelist"><ul class="quotelist"><li>array.parseString('0:0, '1':'1'').asList()</li></ul></ul></ul>[[0, 0], ['1', '1']]
```

As you can see the integer 0 key is changed to string '0' when calling the `asDict` method. Is there a method to keep this as an integer? Thanks again for your great work on this library.
#### 2017-02-04 08:09:24 - ptmcg
Well, that is by design. ParseResults objects support three models to get at the parsed contents: list-like indexing ('result[3]'), dict-like indexing ('result['result_name']') and object attribute notation ('result.result_name').  If you use Dict to create a ParseResults with an integer key of 3, then how should pyparsing interpret 'result[3]'? Is that an integer list index to get the fourth parsed item, or a results name with integer 0? So results names are always strings.

---
## 2017-02-04 17:24:41 - AngshumanGuha - there's a bug in fnumber
right now a single '+' is interpreted as a valid number

a fix:
        inumber = Combine(Optional(Word('+-', max=1)) + Word(nums))               
        fnumber = Combine( inumber +                                              
                           Optional( point + Optional( Word( nums ) ) ) +         
                           Optional( e + inumber))


---
## 2017-02-08 06:43:53 - cdeluna - Multiline Expression
Hi,

I'm  just learing pyparsing and would like to use it to parse out cisco show command files.  The first thing I want to do is extract the inventory information for a device.

Each item is in a two line section which needs to be grouped together and each line has two or more comma delimited keyword/value pairs.

Here is what I've been trying (various permutations) but none give me a single 'record' of the inventory item.  I'm using scanString as I'm reading in a file with a bunch of show commands.

Any pointers in the right direction would be most appreciated!!

Thanks in advance!



    # Open and read in a text file full of show command output
    ParserElement.setDefaultWhitespaceChars(' \t')

    inv_key = Word(alphas)
    inv_value = Word(alphanums)

    first_element = Word('NAME' + ':') + inv_value

    pattern = Combine(OneOrMore(inv_key + ':' + inv_value), adjacent=False)

    first_line = first_element + pattern

    Line = delimitedList(first_line)


    Lines = OneOrMore(Group(Line))

    grammar = Lines
    my_list = grammar.scanString(file_contents)



N7010# show inventory
NAME: 'Chassis',  DESCR: 'Nexus7000 C7010 (10 Slot) Chassis '    
PID: N7K-C7010           ,  VID: V03 ,  SN: JAF1721XYZA         

NAME: 'Slot 1',  DESCR: '1/10 Gbps Ethernet Module'             
PID: N7K-F248XP-25E      ,  VID: V01 ,  SN: JAF1734EFGH          

NAME: 'Slot 2',  DESCR: '1/10 Gbps Ethernet Module'             
PID: N7K-F248XP-25E      ,  VID: V01 ,  SN: JAF1748ABCD          

NAME: 'Slot 5',  DESCR: 'Supervisor Module-2'                   
PID: N7K-SUP2            ,  VID: V03 ,  SN: JAF1804UHM


---
## 2017-03-23 19:47:43 - borismarin - Issues with {{oc.py}} example
First of all, It is always a joy to work with PyParsing!

I have been using the  example grammar from this wiki to parse a C-like language, but have bumped into two issues (not sure if the first one even qualifies as an issue, but I present my solution for it for the sake of completeness:

<ul><li>The regexp for assignments (`=` operator, last in the `operatorPrecedence` list) captures the next character after the `=` due to the regex being used (`'=[^=]'`). This can be inconvenient if no spaces are used between operators and operands. See eg:</li></ul>

    from oc import expr
    
    print(expr.parseString('a = 1').asList())  # ok
    print(expr.parseString('a==1').asList())  # ok
    print(expr.parseString('a=1').asList())  # hmmm

I have changed the regexp to `('(?&lt;!=)=(?!=)'` to cope with this fact, and I guess it would be useful to update the example accordingly if the current behaviour is undesirable.

<ul><li>Function-call like syntax inside `IF` statements is not parsed correctly. For example:</li></ul>

    from oc import ifstmt
    
    print(ifstmt.parseString('if(a == 1){}').asList())  # ok
    print(ifstmt.parseString('if((a+1) == 1){}').asList())  # ok
    print(ifstmt.parseString('if(a() == 1){}').asList())  # bang!

I have tried adding function-call like expressions to the first argument (`baseExpr`) of `operatorPrecedence`, to no avail (which seemed incorrect to start with given that the `Optional` part of `expr` <em>does</em> handle func calls, at least outside if statements).

TL, DR; Could you give me some pointers on how to update  to cope with function calls inside if statements? Thanks!

#### 2017-03-26 20:43:09 - ptmcg
Thanks for the suggestions on the assignment '=' regex, I'll make these changes this evening.

To get function calls working, you will need to modify the base `operand` expression:


    func_call = Group(NAME + LPAR + Group(Optional(delimitedList(expr))) + RPAR)
    operand = func_call | NAME | integer | char | string_

Making this change slows things down quite a bit, so you'll also want to enable packrat parsing, right after the pyparsing import:


    from pyparsing import *
    ParserElement.enablePackrat()


Thanks again for writing, and for using pyparsing!
-- Paul

---
## 2017-04-07 01:14:46 - Lucas-C - Parsing mardown-styled text
Hello !

I've been stuck on this challenge yesterday,
so I'm asking for help here in hope someone could give me some tips & tricks on how to solve this.

My goal is to detect when a string as Markdown-like style markers at the beginning + the end. Examples:

- <strong>a text</strong> =\> bold
- <u><strong>a text</strong></u> =\> bold italic
- <strong><u>a text</u></strong> =\> bold italic
- a <strong>text</strong> =\> just text, I don't want to handle stylers inside strings
- <strong><u>a text</strong></u> =\> just text, style markers are messed-up

Here is what I initially came up with:



    <span class="co1">#!/usr/bin/python3</span>
    
    <span class="kw1">from</span> pyparsing <span class="kw1">import</span> *
    
    Bold <span class="sy0">=</span> Suppress<span class="br0">&#40;</span>Literal<span class="br0">&#40;</span><span class="st0">'**'</span><span class="br0">&#41;</span><span class="br0">&#41;</span>
    Italic <span class="sy0">=</span> Suppress<span class="br0">&#40;</span>Literal<span class="br0">&#40;</span><span class="st0">'__'</span><span class="br0">&#41;</span><span class="br0">&#41;</span>
    
    Text <span class="sy0">=</span> OneOrMore<span class="br0">&#40;</span>Word<span class="br0">&#40;</span>printables<span class="br0">&#41;</span><span class="br0">&#41;</span><span class="br0">&#40;</span><span class="st0">'text'</span><span class="br0">&#41;</span>
    
    StyledText <span class="sy0">=</span> Forward<span class="br0">&#40;</span><span class="br0">&#41;</span>
    BoldText <span class="sy0">=</span> <span class="br0">&#40;</span>Bold + StyledText + Bold<span class="br0">&#41;</span><span class="br0">&#40;</span><span class="st0">'is_bold'</span><span class="br0">&#41;</span>
    ItalicText <span class="sy0">=</span> <span class="br0">&#40;</span>Italic + StyledText + Italic<span class="br0">&#41;</span><span class="br0">&#40;</span><span class="st0">'is_italic'</span><span class="br0">&#41;</span>
    StyledText <span class="sy0">\<\<</span> <span class="br0">&#40;</span>BoldText | ItalicText | Text<span class="br0">&#41;</span>
    
    <span class="kw1">print</span><span class="br0">&#40;</span>StyledText.<span class="me1">parseString</span><span class="br0">&#40;</span><span class="st0">'**toto tata**'</span><span class="sy0">,</span> parseAll<span class="sy0">=</span><span class="kw2">True</span><span class="br0">&#41;</span>.<span class="me1">dump</span><span class="br0">&#40;</span><span class="br0">&#41;</span><span class="br0">&#41;</span>
    <span class="kw1">print</span><span class="br0">&#40;</span>StyledText.<span class="me1">parseString</span><span class="br0">&#40;</span><span class="st0">'**__toto tata__**'</span><span class="sy0">,</span> parseAll<span class="sy0">=</span><span class="kw2">True</span><span class="br0">&#41;</span>.<span class="me1">dump</span><span class="br0">&#40;</span><span class="br0">&#41;</span><span class="br0">&#41;</span>


Then I realized from this SO answer that I needed to make my 'Text' parser stop when it detects a '**' or '__' :


I haven't found any class nor function performing this in pyparsing builtin tools. Should I subclass Token to build my own parser like in this example ?


Regards.

#### 2017-04-07 01:17:42 - Lucas-C
Damn, wikispaces interpreted the syle in my examples ^^

I cannot edit my message so I recopy them there with style markers escaped:


    - **a text** =\> bold
    - **__a text__** =\> bold italic
    - __**a text**__ =\> bold italic
    - a **text** =\> just text, I don't want to handle stylers inside strings
    - __**a text__** =\> just text, style markers are messed-up


#### 2017-04-07 06:31:56 - Lucas-C
I think I've actually come up with a solution, and found a bug at the same occasion.

Here is the bug: 
The full toklist should be passed to the ParseResults constructor, not just its first element:


    <span class="kw2">self</span><span class="br0">&#91;</span>name<span class="br0">&#93;</span> <span class="sy0">=</span> _ParseResultsWithOffset<span class="br0">&#40;</span>ParseResults<span class="br0">&#40;</span>toklist<span class="br0">&#41;</span><span class="sy0">,</span><span class="nu0">0</span><span class="br0">&#41;</span>


And now a solution to my problem:


    <span class="co1">#!/usr/bin/python3</span>
    
    <span class="kw1">from</span> pyparsing <span class="kw1">import</span> Forward<span class="sy0">,</span> Literal<span class="sy0">,</span> OneOrMore<span class="sy0">,</span> Suppress<span class="sy0">,</span> Token<span class="sy0">,</span> Word<span class="sy0">,</span> <span class="kw2">basestring</span><span class="sy0">,</span> printables
    
    <span class="kw1">class</span> StopOnSuffix<span class="br0">&#40;</span>Token<span class="br0">&#41;</span>: <span class="co1"># cannot be a TokenConverter because .postParse does not alter loc</span>
        <span class="kw1">def</span> <span class="kw4">__init__</span><span class="br0">&#40;</span> <span class="kw2">self</span><span class="sy0">,</span> token_matcher<span class="sy0">,</span> suffixes <span class="br0">&#41;</span>:
            <span class="kw2">super</span><span class="br0">&#40;</span>StopOnSuffix<span class="sy0">,</span><span class="kw2">self</span><span class="br0">&#41;</span>.<span class="kw4">__init__</span><span class="br0">&#40;</span><span class="br0">&#41;</span>
            <span class="kw2">self</span>.<span class="me1">name</span> <span class="sy0">=</span> <span class="st0">'StopOnSuffix'</span>
            <span class="kw2">self</span>.<span class="me1">mayReturnEmpty</span> <span class="sy0">=</span> token_matcher.<span class="me1">mayReturnEmpty</span>
            <span class="kw2">self</span>.<span class="me1">mayIndexError</span> <span class="sy0">=</span> token_matcher.<span class="me1">mayIndexError</span>
            <span class="kw2">self</span>.<span class="me1">saveAsList</span> <span class="sy0">=</span> token_matcher.<span class="me1">saveAsList</span>
            <span class="kw2">self</span>.<span class="me1">token_matcher</span> <span class="sy0">=</span> token_matcher
            <span class="kw2">self</span>.<span class="me1">suffixes</span> <span class="sy0">=</span> suffixes
        <span class="kw1">def</span> parseImpl<span class="br0">&#40;</span> <span class="kw2">self</span><span class="sy0">,</span> instring<span class="sy0">,</span> loc<span class="sy0">,</span> doActions<span class="sy0">=</span><span class="kw2">True</span> <span class="br0">&#41;</span>:
            loc<span class="sy0">,</span> tokens <span class="sy0">=</span> <span class="kw2">self</span>.<span class="me1">token_matcher</span>.<span class="me1">parseImpl</span><span class="br0">&#40;</span>instring<span class="sy0">,</span> loc<span class="sy0">,</span> doActions<span class="br0">&#41;</span>
            <span class="kw1">try</span>:
                suffix<span class="sy0">,</span> match_index <span class="sy0">=</span> next<span class="br0">&#40;</span><span class="br0">&#40;</span>suffix<span class="sy0">,</span> i<span class="br0">&#41;</span> <span class="kw1">for</span> i<span class="sy0">,</span> match <span class="kw1">in</span> <span class="kw2">enumerate</span><span class="br0">&#40;</span>tokens<span class="br0">&#41;</span>
                                                       <span class="kw1">for</span> suffix <span class="kw1">in</span> <span class="kw2">self</span>.<span class="me1">suffixes</span> <span class="kw1">if</span> suffix <span class="kw1">in</span> match<span class="br0">&#41;</span>
                match <span class="sy0">=</span> tokens<span class="br0">&#91;</span>match_index<span class="br0">&#93;</span>
                match_trun_len <span class="sy0">=</span> match.<span class="me1">index</span><span class="br0">&#40;</span>suffix<span class="br0">&#41;</span>
                <span class="kw1">if</span> match_trun_len <span class="sy0">\></span> <span class="nu0">0</span>:
                    loc -<span class="sy0">=</span> <span class="kw2">len</span><span class="br0">&#40;</span>match<span class="br0">&#41;</span> - match_trun_len
                    match <span class="sy0">=</span> match<span class="br0">&#91;</span>:match_trun_len<span class="br0">&#93;</span>
                    tokens <span class="sy0">=</span> tokens<span class="br0">&#91;</span>:match_index<span class="br0">&#93;</span> + <span class="br0">&#91;</span>match<span class="br0">&#93;</span> + tokens<span class="br0">&#91;</span>match_index+<span class="nu0">1</span>:<span class="br0">&#93;</span>
            <span class="kw1">except</span> <span class="kw2">StopIteration</span>:
                <span class="kw1">pass</span>
            <span class="kw1">return</span> loc<span class="sy0">,</span> tokens
    
    Bold <span class="sy0">=</span> Suppress<span class="br0">&#40;</span>Literal<span class="br0">&#40;</span><span class="st0">'**'</span><span class="br0">&#41;</span><span class="br0">&#41;</span>
    Italic <span class="sy0">=</span> Suppress<span class="br0">&#40;</span>Literal<span class="br0">&#40;</span><span class="st0">'__'</span><span class="br0">&#41;</span><span class="br0">&#41;</span>
    Text <span class="sy0">=</span> OneOrMore<span class="br0">&#40;</span>Word<span class="br0">&#40;</span>printables<span class="br0">&#41;</span><span class="br0">&#41;</span>
    
    StyledText <span class="sy0">=</span> Forward<span class="br0">&#40;</span><span class="br0">&#41;</span>
    BoldText <span class="sy0">=</span> Bold + StopOnSuffix<span class="br0">&#40;</span>StyledText<span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'**'</span><span class="br0">&#93;</span><span class="br0">&#41;</span><span class="br0">&#40;</span><span class="st0">'is_bold'</span><span class="br0">&#41;</span> + Bold
    ItalicText <span class="sy0">=</span> Italic + StopOnSuffix<span class="br0">&#40;</span>StyledText<span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'__'</span><span class="br0">&#93;</span><span class="br0">&#41;</span><span class="br0">&#40;</span><span class="st0">'is_italic'</span><span class="br0">&#41;</span> + Italic
    StyledText <span class="sy0">\<\<</span> <span class="br0">&#40;</span>BoldText | ItalicText | Text<span class="br0">&#41;</span>
    StyledText.<span class="me1">resultsName</span> <span class="sy0">=</span> <span class="st0">'text'</span>
    StyledText.<span class="me1">saveAsList</span> <span class="sy0">=</span> <span class="kw2">True</span>  <span class="co1"># must be done at this point, not before</span>
    
    <span class="kw1">def</span> <span class="kw3">test</span><span class="br0">&#40;</span>msg<span class="br0">&#41;</span>:
        parsed <span class="sy0">=</span> StyledText.<span class="me1">parseString</span><span class="br0">&#40;</span>msg<span class="sy0">,</span> parseAll<span class="sy0">=</span><span class="kw2">True</span><span class="br0">&#41;</span>
        <span class="co1">#print(parsed.dump())</span>
        <span class="kw1">print</span><span class="br0">&#40;</span><span class="st0">'msg: {} =\> tokens={} is_bold={} is_italic={}'</span>.<span class="me1">format</span><span class="br0">&#40;</span>msg<span class="sy0">,</span> parsed.<span class="me1">text</span><span class="sy0">,</span> <span class="kw2">bool</span><span class="br0">&#40;</span>parsed.<span class="me1">is_bold</span><span class="br0">&#41;</span><span class="sy0">,</span> <span class="kw2">bool</span><span class="br0">&#40;</span>parsed.<span class="me1">is_italic</span><span class="br0">&#41;</span><span class="br0">&#41;</span><span class="br0">&#41;</span>
    <span class="kw3">test</span><span class="br0">&#40;</span><span class="st0">'**a text**'</span><span class="br0">&#41;</span>
    <span class="kw3">test</span><span class="br0">&#40;</span><span class="st0">'**__a text__**'</span><span class="br0">&#41;</span>
    <span class="kw3">test</span><span class="br0">&#40;</span><span class="st0">'__**a text**__'</span><span class="br0">&#41;</span>
    <span class="kw3">test</span><span class="br0">&#40;</span><span class="st0">'a **text**'</span><span class="br0">&#41;</span>
    <span class="kw3">test</span><span class="br0">&#40;</span><span class="st0">'__**a text__**'</span><span class="br0">&#41;</span>


What do you think ? Does it make sense as a Token subclass ?
#### 2017-04-07 06:47:18 - Lucas-C
I guess a cleaner approach to this form of backtracking would be to create an alternative to the 'CharsNotIn' that considers more than 1 character at a time.
#### 2017-04-07 07:04:51 - Lucas-C
But after some tests, such alternative approach does not allow for nested markers.
#### 2017-04-10 04:16:58 - Lucas-C
In the end, the 'StopOnSuffix' class above revealed to be incorrect because we have no way to know how many whitespaces were skipped and hence backtrack properly:


Hence I made another implementation in the same spirit as CharsNotIn : 
It is more limited (the forbidden char sequences are stop words) but it works properly.

---
## 2017-04-14 02:06:52 - pterminator - SkipTo combined with CaselessKeyword gives unexpected results (possible bug)
Hi,

If I combine CaselessKeyword with SkiptTo, SkipTo stops at non-word boundaries for the keyword. The normal Keyword seems not to have this problem.

Reproducer:


    from pyparsing import *
    kw = CaselessKeyword('KEY')
    st=SkipTo(kw)
    st.parseString('hello KEY')
    st.parseString('helloKEY') # false positive here



#### 2017-04-22 20:26:52 - ptmcg
Yes, this looks like a bug, I'll get a fix into 2.2.1, but no ETA on that yet.

Thanks,
-- Paul

---
## 2017-05-30 11:39:49 - qrun - Formal-Tranlastion
Hi 

I have some text-configuration which has a level-relation-ship with space.
Now I have translatet the configuration in a formal-format so i can parse the output better.

Can you tell me maybe, how can I achieve the same result with a cleaner pyparsing implementation? 



    import sys, traceback
    import pyparsing as pp
    
    class Parser(object):
        def __init__(self):
            self.__config_line = []
            self.__config_all = []
            self.__loc_last = 0
            self.__position_last = 0
            self.__dimension = 5
    
            start = pp.OneOrMore(pp.Word(pp.alphanums + '/' + '\.' + '-' + ':'+'!'+'*'))
            a = start+pp.restOfLine
            self.__pattern = pp.Combine(a, joinString='').setParseAction(self.test)
    
        def test(self,s, loc, toks):
    
            position_current = loc - self.__loc_last
            self.__loc_last = loc + 1 + len(toks[0])
            position_delta = position_current - self.__position_last
            self.__position_last = position_current
    
            if position_current == 0:
                self.__config_line = [''] * self.__dimension
                self.__config_line[position_current] = toks[0]
    
            elif position_delta == 0:
                self.__config_line[position_current] = toks[0]
    
            elif position_delta \< 0:
                self.__config_line[position_current:self.__dimension] = [''] * (self.__dimension - 1 - position_current)
                self.__config_line[position_current] = toks[0]
    
            elif position_delta \> 0:
                self.__config_line[self.__position_last + 1:self.__dimension] = [''] * (self.__dimension - 1 - self.__position_last)
                self.__config_line[position_current] = toks[0]
    
            self.__position_last = position_current
            self.__config_all.append(list(self.__config_line))
    
        def parse(self, line):
            try:
                parsed = self.__pattern.searchString(line)
                return self.__config_all
            except pp.ParseException as x:
                #print x
                #return False
                pass
    
    
    if __name__ == '__main__':
        parser = Parser()
    
        test='''first level config parameter 1-n
     section level config parameter 1-n
      thirt level config parameter 1-n
     level level config parameter 1-n
      thirt level  config parameter 1-n
    first level config parameter 1-n'''
        print '## Test String level based ##'
        print '#############################'
        print test
        a = '\n'.join(map('|'.join, parser.parse(test)))
        print '## Test String formal translated ##'
        print '###################################'
        print a



#### 2017-06-04 14:44:19 - ptmcg
Pyparsing is not super-great at parsing whitespace-significant text, but there is a method called 'indentedBlock' to help you define this. 'IndentedBlock' parses text like Python source that uses leading whitespace for grouping.  Here is your parser converted to using indentedBlock:


    indent_stack = [1]
        line_expr = pp.Group(pp.Word(pp.alphas) + 'level' + pp.empty + pp.restOfLine)
        line_expr.setName('line')
        section = pp.Forward().setName('section')
        block = pp.indentedBlock(section, indent_stack)
        section \<\<= line_expr + pp.Optional(block)
        parser = pp.OneOrMore(section)
    
        test='''\
        first level config parameter 1-n
         section level config parameter 1-n
          thirt level config parameter 1-n
         level level config parameter 1-n
          thirt level  config parameter 1-n
        first level config parameter 1-n
        first level config parameter 1-n
        '''
    
        print('## Test String level based ##')
        print('#############################')
        print(test)
        print('## Test String formal translated ##')
        print('###################################')
        #~ a = '\n'.join(map('|'.join, parser.parse(test)))
        #~ print(a)
        res = parser.parseString(test)
        res.pprint()

Prints:


    [['first', 'level', 'config parameter 1-n'],
     [[['section', 'level', 'config parameter 1-n'],
       [[['thirt', 'level', 'config parameter 1-n']]]],
      [['level', 'level', 'config parameter 1-n'],
       [[['thirt', 'level', 'config parameter 1-n']]]]],
     ['first', 'level', 'config parameter 1-n'],
     ['first', 'level', 'config parameter 1-n']]

You have to provide an external list that indentedBlock will use to track the stack of previous indents, so that unindents get closed properly.

HTH,
-- Paul

---
## 2017-06-26 16:35:01 - EvanHub - Prevent an element from matching dependent on context
Is there any way to write 'disable' that would work here? Right now, for the equivalent of this code in Coconut, I just effectively re-write the whole expr code twice (once with op1 and once without), but the Coconut code that does that has become really complicated such that that is no longer a viable solution. Any thoughts? 

```python
from pyparsing import (
    Literal,
    ZeroOrMore,
    Forward,
    stringStart,
    stringEnd,
)

def disable(item, elem):
    '''Prevent elem from matching inside of item.'''
    return item  # what to do here?

atom = Literal('a')

op1 = Literal('*')
op2 = Literal('+')

no1open = Literal('(')
no1close = Literal(')')

expr = Forward()

expr0 = atom | no1open + disable(expr, op1) + no1close
expr1 = expr0 + ZeroOrMore(op1 + expr0)
expr \<\<= expr1 + ZeroOrMore(op2 + expr1)

grammar = stringStart + expr + stringEnd

def match_in(text):
    '''Determines if there is a match for grammar in text.'''
    for result in grammar.parseWithTabs().scanString(text):
        return True
    return False

assert match_in('a * a')
assert match_in('a + a')
assert match_in('a * a + a * a')
assert match_in('a + (a + a)')
assert match_in('a * (a + a)')
assert not match_in('a + (a * a)')  # fails, because disable does nothing
```

#### 2017-06-26 16:36:31 - EvanHub
Wow, this formatting is the worst. Here's a gist so you don't have to read that: 
#### 2017-06-26 21:03:12 - ptmcg
This is odd to me - why is '*' not permitted in parenthesized groups? Off the top of my head, you'll need to define a different kind of expression for the intra-() groups that only supports '+' operation.

In any event, I got this to work by splitting out from the infixNotation expression those operators that are not allowed in ()'s.



    import pyparsing as pp
    
    atom = pp.oneOf(list(pp.alphas)) | pp.pyparsing_common.integer
    
    # too lazy to write recursive grammar, this will handle parentheticals
    add_expr = pp.infixNotation(atom,
        [
        ('+', 2, pp.opAssoc.LEFT,),
        ])
    
    # since this is done outside the infixNotation expression, not permitted in ()'s, only at top-most level
    expr = add_expr + pp.ZeroOrMore('*' + add_expr)
    
    expr.runTests('''\
        a * a
        a + a
        a * a + a * a
        a + (a + a)
        a * (a + a)
        a + (a * a)
    ''')


#### 2017-06-26 23:09:54 - EvanHub
It's just a toy example to showcase the difficulty, the actual use case is too complicated to try to completely write out here. Thus, unfortunately, for my full use case I can't just rewrite the grammar like you did, though I agree that works in this case. I really do need something to put inside that function. I've been hacking away at this, though, and I managed to get it working with a couple custom tokens, though it's not the most elegant solution I've ever seen. If you have any thoughts on how it could be improved, it'd be much appreciated. Here's the new version: 
#### 2017-06-28 01:17:45 - ptmcg
Is this any better?


    disable = lambda x, disallowed: x().addCondition(lambda t: not any(map(disallowed.matches, t)))
    expr_no_op1 = disable(expr, op1)

Not super-great, as it re-parses each token to see if it matches the disallowed expression, which works for this simple case but I'm not so sure about your larger grammar.

Also, I think that in place of match_in, you can just use expr.matches.  Or use expr.runTests as I did above. (You can use the returned values from runTests to do asserts - for tests that are supposed to fail, pass failTests=True and then runTests will only return success as True if all the test strings fail.)
#### 2017-06-28 01:22:36 - ptmcg
Wow, I used 'super-great' in two consecutive comment threads. Sad.
runTests doc and examples at 
#### 2017-06-28 01:29:01 - ptmcg


    assert grammar.runTests('''\
        a * a
        a + a
        a * a + a * a
        a + (a + a)
        a * (a + a)
        ''', fullDump=False)[0]
    
    assert grammar.runTests('''\
        a + (a + (a * a))
        ''', fullDump=False, failureTests=True)[0]


#### 2017-06-28 01:30:05 - ptmcg
Prints:


    a * a
    ['a', '*', 'a']
    
    a + a
    ['a', '+', 'a']
    
    a * a + a * a
    ['a', '*', 'a', '+', 'a', '*', 'a']
    
    a + (a + a)
    ['a', '+', ['(', 'a', '+', 'a', ')']]
    
    a * (a + a)
    ['a', '*', ['(', 'a', '+', 'a', ')']]
    
    a + (a + (a * a))
      ^
    FAIL: Expected stringEnd (at char 2), (line:1, col:3)


#### 2017-06-28 01:30:54 - ptmcg
Oops, I had also added a Group in expr0: expr0 = atom | Group(no1open + expr_no_op1 + no1close)
#### 2017-07-04 12:25:25 - EvanHub
Yeah, that's definitely helpful! Like you said, it does require the string to get parsed twice, though, which is fairly inefficient. If you're curious, I ended up going with this: 

Being able to wrap a token in a context manager was all I really needed. Maybe 'Wrap' is something you might want to consider including?

On an unrelated note, I'm thinking of rewriting PyParsing in Cython to try to squeeze out some extra performance benefits for Coconut. I'll probably host it on GitHub and put it up as cpyparsing or some such thing on PyPI, if you don't mind.
#### 2017-07-05 06:20:48 - ptmcg
A Cythonic pyparsing has been worked on in the past (I say this not to discourage because of prior activity but to encourage as to feasibility), I'll try to track it down from prior efforts.

I'll have to think about the contextmanager bit - I'll need to include it in a Py2.6-compatible form while I'm still supporting back to that version in a single code base, but I'm especially fond of the contextmanager concept, and wrapping an expression in a larger expression is consistent with pyparsing's philosophy. Thanks for the suggestions!

---
## 2017-08-03 10:43:07 - ferenc0521 - Group result question
I'm parsing  CREATE INDEX sql statements as :
create index dft_inst_strm_dft_snpsht_el_idx on defect_instance (stream_defect_id, snapshot_element_id);
I'm parsing the 'on defect_instance (stream_defect_id, snapshot_element_id)' part with the grammar:

ON = Keyword('on', caseless=True).addParseAction(upcaseTokens)
LPAREN= Suppress('(')
RPAREN= Suppress(')')

idxspec = ON + ident + LPAREN + Group(delimitedList(ident)) + RPAREN   
....
result = idxspec.parseString(stmt[3][0])
indices.append([stmt[2] , result[1] , len(result[2]) , result[2]])
....
The returned result[2] (for the Group(delimitedList(ident))) prints as (['stream_defect_id', 'snapshot_element_id'], {}) as in the appended array:

['dft_inst_strm_dft_snpsht_el_idx', 'defect_instance', 2, (['stream_defect_id', 'snapshot_element_id'], {})]

I expected an ['stream_defect_id', 'snapshot_element_id'] for result[2], but looks like a tuple with the extra empty dictionary added.
Is there an explanation, and a way to extract the 'naked' array without the empty dict?

#### 2017-08-03 12:45:49 - ptmcg
There is no array ('list' actually) and there is no dict. What you are seeing is the repr representation of pyparsing's parse output object, ParseResults. Since ParseResults objects can be accessed in both list and dict forms, the repr output shows the list elements as a list and any named elements as a dict. You can iterate over the ParseResults, index into them, invoke len() on them, just like any list, or invoke keys(), items(), values(), etc. just like a dict. See more info about ParseResults capabilities at  .  If you *must* have a list or dict, this class also supports asList() and asDict() methods, but you may be able to do without them. Please give it a shot and just use this as if it were a list, for instance, try printing '','.join(result[2])'.
#### 2017-08-03 18:12:31 - ferenc0521
Thanks,
     result[2].asList()] worked perfectly.
The result indices feels better with the plain list:
....
['file_inst_parent_idx', 'file_instance', 1, ['parent_id']]
['file_inst_src_data_file_idx', 'file_instance', 2, ['source_data_id', 'file_id']]
['file_inst_strm_file_idx', 'file_instance', 1, ['stream_file_id']]
...

---
## 2017-08-13 16:19:26 - ferenc0521 - schemaSQL.parseFile(f) fails if parseAll=True attemted


    result = schemaSQL.parseFile(f,parseAll=True)

fails with TypeError: parseFile() got an unexpected keyword argument 'parseAll', 
while doc says:    def parseFile( self, file_or_filename, parseAll=False ): 

Any pointers?

#### 2017-08-13 16:59:27 - ptmcg
According to the CHANGES file, it looks like that named arg was added to parseFile in version 1.5.1, back in '08. Are you on an old version of pyparsing?
#### 2017-08-13 19:41:27 - ferenc0521
\>python -m pip list   says:
...
pyparsing (2.2.0)
...

C:\Users\flazar\>python -V
Python 2.7
I was trying to get some plots with numpy and mathplotlib, and I have some unsolved mysteries with the windows 64bit python and some win32 libraries, so I'm not 100% sure the plumbing is flawless.
#### 2017-08-13 19:52:49 - ptmcg
Hm, matplotlib used to bundle pyparsing as part of its mathtext module, so you may be having conflicts there. In your code, add:


    import pyparsing; print pyparsing.__version__


If it turns out that you are having conflicts with matplotlib's pyparsing, then be sure to import pyparsing in your module before importing matplotlib. In this way, the latest pyparsing will get imported first, and the import in matplotlib will be a no-op. I *think* matplotlib will work okay with an updated pyparsing, but if you don't use mathtext, then it won't really matter.
#### 2017-08-13 20:14:13 - ferenc0521
1.4.11
Thank you, you are right as always :)
#### 2017-08-14 07:46:02 - ferenc0521
Sorry for the n00b question, but how can I rectify this?

C:\Python27\Lib\site-packages\pyparsing.py has
    def parseFile( self, file_or_filename, parseAll=False ):

And the C:\Python27\Lib\site-packages\pyparsing-2.2.0-py2.7.egg-info folder has some text files, but didn't find traces of the earlier version.
Any 'tools of the trade' advice?
Would uninstalling the whole python and installing -say- activepython distro would help?
#### 2017-08-17 21:20:10 - ptmcg
I've started sorting out these kinds of packaging issues using virtualenv, which allows you a lot more flexibility to try installing/removing packages without messing up your system environment. If you are absolutely desperate, pyparsing's code is just a single .py file, so you can extract that and put it explicitly in your PYTHONPATH wherever you choose - but do this only as a last resort, or as a temporary workaround until you get your overall packaging bits resolved.
#### 2017-08-18 10:42:20 - ferenc0521
Thanks for your help again!!!
Haven't yet  mastered virtualenv (I installed virtualenvwrapper-win on windows), but tracked down and deleted all the pyparsing.pyc-s windows could find, and checked the <u>version</u> in every pyparsing.py source windows could find.
To my great embarrassment  the ONLY 1.4.11 was the one I downloaded from somewhere during internet search and put it right next to my source in the eclipse workspace.
The others ranged from 2.0.1.10 - 2.2.0 (I recently installed with pip).
After clearing that and restarting eclips the version is 2.2.0 (Yayyyy!)
No if only I could fix the tcl/tk so mathplotlip could work :)

---
## 2017-08-16 08:12:45 - mdemi - Odd .copy() behaviour
I've finally made the jump from 1.5.2 or so to 2.1.10, and what kept me
from upgrading back then bites me again: .copy() changes the behaviour
of ParserElements since 1.5.2:

Here's an example:



    import pprint
    from pyparsing import Word, ZeroOrMore, alphas
    
    def get_grammar():
        vanishing = Word(alphas)
        item = 'foo' | vanishing
        item_seq = item + ZeroOrMore( item )
        return locals()
    
    def enable_tree(syms):
        for name, ob in syms.iteritems():
            ob.setParseAction(lambda s, p, t, name=name: (name,)+tuple(t))
    
    if __name__=='__main__':
        g = get_grammar()
        enable_tree(g)
        pprint.pprint(g['item_seq'].parseString('foo bar')[0])


If you ignore the plumbing, it's a trivial sequence grammar.  The stuff
is arranged to spit out a representation of the parse tree, and if you
try it, you'll see it's printing the expected



    ('item_seq', ('item', 'foo'), ('item', ('vanishing', 'bar')))


However, if you now change the grammar to:



    def get_grammar():
        vanishing = Word(alphas)
        item = 'foo' | vanishing
        item = item.copy()       # \<--- inserting a call to copy
        item_seq = item + ZeroOrMore( item )
        return locals()


pyparsing doesn't 'see' the 'vanishing' nonterminal any more, and the
output is:



    ('item_seq', ('item', 'foo'), ('item', 'bar'))


In more complex grammars, you'll see that only the level below the
copied (or, more dramatically, setResultsName-d) element is swallowed --
rules deeper down are again correctly represented.

Is this expected behaviour?  I'm asking because apparently no one got
hit by this in the past eight years apart from me, so somehow I suspect
I'm being stupid.  Am I?

#### 2017-08-17 05:10:31 - mdemi
Ok – with a bit of poking around I understodd how this behaviour comes about: the copy() does a deep copy or the dependent expressions.  The .addParseAction in enable_tree then hits a 'dead', unused ParserElement.

Now, I'd really love to be able to attach actions after the fact.  I'd still like to use .setResultsName (which does an implicit copy).  I *think* what I want is shallow copies of self.exprs; current pyparsing does an explicit copy since 1.5.3 (or somesuch) around line 3324:



    ret.exprs = [e.copy() for e in self.exprs]


Does anyone remember what would break if I restored the previous behaviour, which, I think, essentially is equivalent to



    ret.exprs = self.exprs[:]


(depending on copy.copy() semantics, I guess).
#### 2017-08-17 21:28:19 - ptmcg
My first thought is that this is actually a bug in copy(). I'll look at this in more detail this weekend. I'll also take a look at what you have described and see if there is a reasonable workaround or alternative.
#### 2017-08-29 05:07:06 - ptmcg
Haven't forgotten you - I looked back through history to see what the impetus was for this change, but did not see the specific bug or case that inspired it. I did make your change and reran my unit tests, and all appears to be okay, but I still want to revisit my history dive.

Thanks for your patience,
-- Paul

---
## 2017-08-27 19:25:52 - vacaut - += operator and user function for math equation
I am new to parsing and have just come accross this tool which looks great.

For my work, I need to parse multiple lines of math equations with variables and user defined functions inside. For example, with 3 lines of string:
x = 1
y = Max(1,2)
x += y
I want to be able to get x = 3 and y = 2 at the end.

Below is my attempt on this. I am just trying to make a slight modification to the fourFn.py and SimpleCalc.py examples in the wiki page.


    <span class="kw1">import</span> <span class="kw3">operator</span>
    <span class="kw1">from</span> pyparsing <span class="kw1">import</span> Literal<span class="sy0">,</span>Word<span class="sy0">,</span>Combine<span class="sy0">,</span>Optional<span class="sy0">,</span>ZeroOrMore<span class="sy0">,</span>Forward<span class="sy0">,</span>nums<span class="sy0">,</span>\
        alphas
    <span class="kw1">from</span> <span class="kw3">collections</span> <span class="kw1">import</span> defaultdict
    
    <span class="kw1">def</span> main<span class="br0">&#40;</span><span class="br0">&#41;</span>:
        <span class="kw1">global</span> exprStack
        exprStack <span class="sy0">=</span> <span class="br0">&#91;</span><span class="br0">&#93;</span>
        <span class="kw1">global</span> varStack
        varStack  <span class="sy0">=</span> <span class="br0">&#91;</span><span class="br0">&#93;</span>
        <span class="kw1">global</span> variables
        variables <span class="sy0">=</span> defaultdict<span class="br0">&#40;</span><span class="kw2">float</span><span class="br0">&#41;</span>
        l <span class="sy0">=</span> <span class="br0">&#91;</span><span class="st0">'x=1'</span><span class="sy0">,</span><span class="st0">'y=abs(2)'</span><span class="sy0">,</span> <span class="st0">'x+=y'</span><span class="br0">&#93;</span>
        <span class="kw1">for</span> item <span class="kw1">in</span> l:
            source <span class="sy0">=</span> item
            L <span class="sy0">=</span> BNF<span class="br0">&#40;</span><span class="br0">&#41;</span>.<span class="me1">parseString</span><span class="br0">&#40;</span> source <span class="br0">&#41;</span>
            <span class="kw1">print</span><span class="br0">&#40;</span>L<span class="br0">&#41;</span>
            result <span class="sy0">=</span> evaluateStack<span class="br0">&#40;</span> exprStack<span class="br0">&#91;</span>:<span class="br0">&#93;</span> <span class="br0">&#41;</span>
            <span class="kw1">print</span><span class="br0">&#40;</span>varStack<span class="br0">&#41;</span>
            <span class="kw1">print</span><span class="br0">&#40;</span>result<span class="br0">&#41;</span>
            variables<span class="br0">&#91;</span>varStack.<span class="me1">pop</span><span class="br0">&#40;</span><span class="br0">&#41;</span><span class="br0">&#93;</span><span class="sy0">=</span>result
            <span class="kw1">print</span><span class="br0">&#40;</span>variables<span class="br0">&#41;</span>
    
    <span class="kw1">def</span> Scalar<span class="br0">&#40;</span>x<span class="br0">&#41;</span>:
        <span class="kw1">return</span> x
    
    <span class="kw1">def</span> pushFirst<span class="br0">&#40;</span> strg<span class="sy0">,</span> loc<span class="sy0">,</span> toks <span class="br0">&#41;</span>:
        exprStack.<span class="me1">append</span><span class="br0">&#40;</span> toks<span class="br0">&#91;</span><span class="nu0">0</span><span class="br0">&#93;</span> <span class="br0">&#41;</span>
    
    <span class="kw1">def</span> assignVar<span class="br0">&#40;</span> strg<span class="sy0">,</span> loc<span class="sy0">,</span> toks <span class="br0">&#41;</span>:
        varStack.<span class="me1">append</span><span class="br0">&#40;</span> toks<span class="br0">&#91;</span><span class="nu0">0</span><span class="br0">&#93;</span> <span class="br0">&#41;</span>
    
    bnf <span class="sy0">=</span> <span class="kw2">None</span>
    <span class="kw1">def</span> BNF<span class="br0">&#40;</span><span class="br0">&#41;</span>:
        <span class="st0">'''
        expop   :: '^'
        multop  :: '*' | '/'
        addop   :: '+' | '-'
        integer :: ['+' | '-'] '0'..'9'+
        atom    :: real | fn '(' expr ')' | '(' expr ')'
        factor  :: atom [ expop factor ]*
        term    :: factor [ multop factor ]*
        expr    :: term [ addop term ]*
        iaddop  :: '+='
        assign  :: '='
        '''</span>
        <span class="kw1">global</span> bnf
        <span class="kw1">if</span> <span class="kw1">not</span> bnf:
            point <span class="sy0">=</span> Literal<span class="br0">&#40;</span> <span class="st0">'.'</span> <span class="br0">&#41;</span>
            fnumber <span class="sy0">=</span> Combine<span class="br0">&#40;</span> Word<span class="br0">&#40;</span> <span class="st0">'+-'</span>+nums<span class="sy0">,</span> nums <span class="br0">&#41;</span> + 
                               Optional<span class="br0">&#40;</span> point + Optional<span class="br0">&#40;</span> Word<span class="br0">&#40;</span> nums <span class="br0">&#41;</span> <span class="br0">&#41;</span> <span class="br0">&#41;</span><span class="br0">&#41;</span>
            ident <span class="sy0">=</span> Word<span class="br0">&#40;</span>alphas+<span class="st0">'_'</span><span class="sy0">,</span> alphas+nums+<span class="st0">'_'</span><span class="br0">&#41;</span>
    
            plus  <span class="sy0">=</span> Literal<span class="br0">&#40;</span> <span class="st0">'+'</span> <span class="br0">&#41;</span>
            minus <span class="sy0">=</span> Literal<span class="br0">&#40;</span> <span class="st0">'-'</span> <span class="br0">&#41;</span>
            mult  <span class="sy0">=</span> Literal<span class="br0">&#40;</span> <span class="st0">'*'</span> <span class="br0">&#41;</span>
            div   <span class="sy0">=</span> Literal<span class="br0">&#40;</span> <span class="st0">'/'</span> <span class="br0">&#41;</span>
            lpar  <span class="sy0">=</span> Literal<span class="br0">&#40;</span> <span class="st0">'('</span> <span class="br0">&#41;</span>.<span class="me1">suppress</span><span class="br0">&#40;</span><span class="br0">&#41;</span>
            rpar  <span class="sy0">=</span> Literal<span class="br0">&#40;</span> <span class="st0">')'</span> <span class="br0">&#41;</span>.<span class="me1">suppress</span><span class="br0">&#40;</span><span class="br0">&#41;</span>
            addop  <span class="sy0">=</span> plus | minus
            multop <span class="sy0">=</span> mult | div
            expop <span class="sy0">=</span> Literal<span class="br0">&#40;</span> <span class="st0">'^'</span> <span class="br0">&#41;</span>
            assign <span class="sy0">=</span> Literal<span class="br0">&#40;</span> <span class="st0">'='</span> <span class="br0">&#41;</span>
            iaddop <span class="sy0">=</span> Literal<span class="br0">&#40;</span><span class="st0">'+='</span><span class="br0">&#41;</span>
    
            expr <span class="sy0">=</span> Forward<span class="br0">&#40;</span><span class="br0">&#41;</span>
            atom <span class="sy0">=</span> <span class="br0">&#40;</span> fnumber | ident + lpar + expr + rpar | ident <span class="br0">&#41;</span>.<span class="me1">setParseAction</span><span class="br0">&#40;</span>pushFirst<span class="br0">&#41;</span> | <span class="br0">&#40;</span> lpar + expr.<span class="me1">suppress</span><span class="br0">&#40;</span><span class="br0">&#41;</span> + rpar <span class="br0">&#41;</span>
    
            <span class="co1"># by defining exponentiation as 'atom [ ^ factor ]...' instead of 'atom [ ^ atom ]...', we get right-to-left exponents, instead of left-to-righ</span>
            <span class="co1"># that is, 2^3^2 = 2^(3^2), not (2^3)^2.</span>
            factor <span class="sy0">=</span> Forward<span class="br0">&#40;</span><span class="br0">&#41;</span>
            factor <span class="sy0">\<\<</span> atom + ZeroOrMore<span class="br0">&#40;</span> <span class="br0">&#40;</span> expop + factor <span class="br0">&#41;</span>.<span class="me1">setParseAction</span><span class="br0">&#40;</span> pushFirst <span class="br0">&#41;</span> <span class="br0">&#41;</span>
    
            term <span class="sy0">=</span> factor + ZeroOrMore<span class="br0">&#40;</span> <span class="br0">&#40;</span> multop + factor <span class="br0">&#41;</span>.<span class="me1">setParseAction</span><span class="br0">&#40;</span> pushFirst <span class="br0">&#41;</span> <span class="br0">&#41;</span>
            expr <span class="sy0">\<\<</span> term + ZeroOrMore<span class="br0">&#40;</span> <span class="br0">&#40;</span> addop + term <span class="br0">&#41;</span>.<span class="me1">setParseAction</span><span class="br0">&#40;</span> pushFirst <span class="br0">&#41;</span> <span class="br0">&#41;</span>
            bnf <span class="sy0">=</span>  ident.<span class="me1">setParseAction</span><span class="br0">&#40;</span>assignVar<span class="br0">&#41;</span> + <span class="br0">&#40;</span>assign | iaddop.<span class="me1">setParseAction</span><span class="br0">&#40;</span> pushFirst <span class="br0">&#41;</span><span class="br0">&#41;</span> + expr
        <span class="kw1">return</span> bnf
    
    <span class="co1"># map operator symbols to corresponding arithmetic operations</span>
    opn <span class="sy0">=</span> <span class="br0">&#123;</span> <span class="st0">'+'</span> : <span class="kw3">operator</span>.<span class="me1">add</span><span class="sy0">,</span>
            <span class="st0">'-'</span> : <span class="kw3">operator</span>.<span class="me1">sub</span><span class="sy0">,</span>
            <span class="st0">'*'</span> : <span class="kw3">operator</span>.<span class="me1">mul</span><span class="sy0">,</span>
            <span class="st0">'/'</span> : <span class="kw3">operator</span>.<span class="me1">truediv</span><span class="sy0">,</span>
            <span class="st0">'^'</span> : <span class="kw3">operator</span>.<span class="kw2">pow</span><span class="sy0">,</span>
            <span class="st0">'+='</span> : <span class="kw3">operator</span>.<span class="me1">iadd</span><span class="br0">&#125;</span>
    fn  <span class="sy0">=</span> <span class="br0">&#123;</span> <span class="st0">'Max'</span> : <span class="kw2">max</span><span class="sy0">,</span>
            <span class="st0">'Min'</span> : <span class="kw2">min</span><span class="sy0">,</span>
            <span class="st0">'abs'</span> : <span class="kw2">abs</span><span class="sy0">,</span>
           <span class="st0">'Scalar'</span> : Scalar<span class="br0">&#125;</span>
    
    <span class="kw1">def</span> evaluateStack<span class="br0">&#40;</span> s <span class="br0">&#41;</span>:
        op <span class="sy0">=</span> s.<span class="me1">pop</span><span class="br0">&#40;</span><span class="br0">&#41;</span> 
        <span class="kw1">if</span> op <span class="kw1">in</span> <span class="st0">'+-*/^'</span> <span class="kw1">or</span> op <span class="kw1">in</span> <span class="st0">'+='</span>:
            op2 <span class="sy0">=</span> evaluateStack<span class="br0">&#40;</span> s <span class="br0">&#41;</span>
            op1 <span class="sy0">=</span> evaluateStack<span class="br0">&#40;</span> s <span class="br0">&#41;</span>
            <span class="kw1">return</span> opn<span class="br0">&#91;</span>op<span class="br0">&#93;</span><span class="br0">&#40;</span> op1<span class="sy0">,</span> op2 <span class="br0">&#41;</span>
        <span class="kw1">elif</span> op <span class="kw1">in</span> fn:
            <span class="kw1">return</span> fn<span class="br0">&#91;</span>op<span class="br0">&#93;</span><span class="br0">&#40;</span> evaluateStack<span class="br0">&#40;</span> s <span class="br0">&#41;</span> <span class="br0">&#41;</span>
        <span class="kw1">elif</span> op <span class="kw1">in</span> variables:
            <span class="kw1">return</span> variables<span class="br0">&#91;</span>op<span class="br0">&#93;</span>        
        <span class="kw1">else</span>:
            <span class="kw1">return</span> <span class="kw2">float</span><span class="br0">&#40;</span> op <span class="br0">&#41;</span>
    
    <span class="kw1">if</span> __name__ <span class="sy0">==</span> <span class="st0">'__main__'</span>:
        main<span class="br0">&#40;</span><span class="br0">&#41;</span>


But I have faced two issues.
1. The += operator is not working as expected. With input string as ['x=1','y=2', 'x+=y'], I still get x= 1 in the end. \<-- defaultdict(\<class 'float'\>, {'x': 1.0, 'y': 2.0}) 
2. My user defined funciton name will have the same name convention as the variable name convention. The only difference is that the function will have parentheses followed. I tried to modify the atom definition but it is not working as expected. With input string as ['x=1','y=abs(2)', 'x+=y'], I got a ValueError: could not convert string to float: 'y'.

Would you help to shred some lights on how to fix the problem? Thanks.

#### 2017-09-02 06:28:49 - vacaut
For my work, there is no exponential operation, and this makes things easier. But on the other hand, the user defined function is exactly like a python function and can take argument such as list or keyword argument (name = value). i plan to directly write those functions in python, so i just need to call those functions with parsed argument list.
I have read more examples such as arith.py and excelExpr.py and discussion in this forum. And it seems infixNotation helps to simplify the definition of operators. But i am puzzled whether i should treat the brackets as an operator and if so how to do that.
I have tried a bit with new style of code like below by making list a kind of parseelement instead of an operator


    <span class="kw1">from</span> pyparsing <span class="kw1">import</span> *
    
    compOp <span class="sy0">=</span> oneOf<span class="br0">&#40;</span><span class="st0">'\< \> \>= \<='</span><span class="br0">&#41;</span>
    multOp <span class="sy0">=</span> oneOf<span class="br0">&#40;</span><span class="st0">'* /'</span><span class="br0">&#41;</span>
    addOp <span class="sy0">=</span> oneOf<span class="br0">&#40;</span><span class="st0">'+ -'</span><span class="br0">&#41;</span>
    augassignOp <span class="sy0">=</span> Literal<span class="br0">&#40;</span><span class="st0">'+='</span><span class="br0">&#41;</span>
    
    EQ<span class="sy0">,</span>LPAR<span class="sy0">,</span>RPAR<span class="sy0">,</span>LBRA<span class="sy0">,</span>RBRA <span class="sy0">=</span> <span class="kw2">map</span><span class="br0">&#40;</span>Suppress<span class="sy0">,</span> <span class="st0">'=()[]'</span><span class="br0">&#41;</span>
    
    varname <span class="sy0">=</span> Regex<span class="br0">&#40;</span>r<span class="st0">'[a-zA-Z_][a-zA-Z0-9_]*'</span><span class="br0">&#41;</span>
    fname <span class="sy0">=</span> Regex<span class="br0">&#40;</span>r<span class="st0">'[a-zA-Z][a-zA-Z0-9_]*'</span><span class="br0">&#41;</span>
    decimalnumber <span class="sy0">=</span> Regex<span class="br0">&#40;</span>r<span class="st0">'[+-]?<span class="es0">\d</span>+(<span class="es0">\.</span><span class="es0">\d</span>*)?'</span><span class="br0">&#41;</span>
    
    expr <span class="sy0">=</span> Forward<span class="br0">&#40;</span><span class="br0">&#41;</span>
    listmaker <span class="sy0">=</span> Group<span class="br0">&#40;</span>LBRA + delimitedList<span class="br0">&#40;</span>expr<span class="br0">&#41;</span> + RBRA<span class="br0">&#41;</span><span class="br0">&#40;</span><span class="st0">'list'</span><span class="br0">&#41;</span>
    funccall <span class="sy0">=</span> Group<span class="br0">&#40;</span>fname<span class="br0">&#40;</span><span class="st0">'fname'</span><span class="br0">&#41;</span> + LPAR + Group<span class="br0">&#40;</span>delimitedList<span class="br0">&#40;</span>expr<span class="br0">&#41;</span><span class="br0">&#41;</span><span class="br0">&#40;</span><span class="st0">'arglist'</span><span class="br0">&#41;</span> + RPAR<span class="br0">&#41;</span>
    operand <span class="sy0">=</span> decimalnumber | listmaker | funccall | varname
    expr <span class="sy0">\<\<=</span> infixNotation<span class="br0">&#40;</span>operand<span class="sy0">,</span>
        <span class="br0">&#91;</span>
        <span class="br0">&#40;</span>multOp<span class="sy0">,</span> <span class="nu0">2</span><span class="sy0">,</span> opAssoc.<span class="me1">LEFT</span><span class="br0">&#41;</span><span class="sy0">,</span>
        <span class="br0">&#40;</span>addOp<span class="sy0">,</span> <span class="nu0">2</span><span class="sy0">,</span> opAssoc.<span class="me1">LEFT</span><span class="br0">&#41;</span><span class="sy0">,</span>
        <span class="br0">&#40;</span>compOp<span class="sy0">,</span> <span class="nu0">2</span><span class="sy0">,</span> opAssoc.<span class="me1">LEFT</span><span class="br0">&#41;</span><span class="sy0">,</span>
    <span class="co1">#    (augassignOp, 2, opAssoc.LEFT),</span>
        <span class="br0">&#93;</span><span class="br0">&#41;</span>
    
    l <span class="sy0">=</span> <span class="br0">&#91;</span><span class="st0">'cond(1,select(4,[2, 3]))'</span><span class="br0">&#93;</span>
    
    <span class="kw1">for</span> item <span class="kw1">in</span> l:
        source <span class="sy0">=</span> item
        expr.<span class="me1">runTests</span><span class="br0">&#40;</span>source<span class="br0">&#41;</span>


The parsing seems to work as I got below result:


    cond<span class="br0">&#40;</span><span class="nu0">1</span><span class="sy0">,</span><span class="kw3">select</span><span class="br0">&#40;</span><span class="nu0">4</span><span class="sy0">,</span><span class="br0">&#91;</span><span class="nu0">2</span><span class="sy0">,</span> <span class="nu0">3</span><span class="br0">&#93;</span><span class="br0">&#41;</span><span class="br0">&#41;</span>
    <span class="br0">&#91;</span><span class="br0">&#91;</span><span class="st0">'cond'</span><span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'1'</span><span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'select'</span><span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'4'</span><span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'2'</span><span class="sy0">,</span> <span class="st0">'3'</span><span class="br0">&#93;</span><span class="br0">&#93;</span><span class="br0">&#93;</span><span class="br0">&#93;</span><span class="br0">&#93;</span><span class="br0">&#93;</span>
    <span class="br0">&#91;</span><span class="nu0">0</span><span class="br0">&#93;</span>:
      <span class="br0">&#91;</span><span class="st0">'cond'</span><span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'1'</span><span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'select'</span><span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'4'</span><span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'2'</span><span class="sy0">,</span> <span class="st0">'3'</span><span class="br0">&#93;</span><span class="br0">&#93;</span><span class="br0">&#93;</span><span class="br0">&#93;</span><span class="br0">&#93;</span>
      - arglist: <span class="br0">&#91;</span><span class="st0">'1'</span><span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'select'</span><span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'4'</span><span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'2'</span><span class="sy0">,</span> <span class="st0">'3'</span><span class="br0">&#93;</span><span class="br0">&#93;</span><span class="br0">&#93;</span><span class="br0">&#93;</span>
        <span class="br0">&#91;</span><span class="nu0">0</span><span class="br0">&#93;</span>:
          <span class="nu0">1</span>
        <span class="br0">&#91;</span><span class="nu0">1</span><span class="br0">&#93;</span>:
          <span class="br0">&#91;</span><span class="st0">'select'</span><span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'4'</span><span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'2'</span><span class="sy0">,</span> <span class="st0">'3'</span><span class="br0">&#93;</span><span class="br0">&#93;</span><span class="br0">&#93;</span>
          - arglist: <span class="br0">&#91;</span><span class="st0">'4'</span><span class="sy0">,</span> <span class="br0">&#91;</span><span class="st0">'2'</span><span class="sy0">,</span> <span class="st0">'3'</span><span class="br0">&#93;</span><span class="br0">&#93;</span>
            - <span class="kw2">list</span>: <span class="br0">&#91;</span><span class="st0">'2'</span><span class="sy0">,</span> <span class="st0">'3'</span><span class="br0">&#93;</span>
          - fname: <span class="st0">'select'</span>
      - fname: <span class="st0">'cond'</span>


But i am puzzled how to pass the argument back to the function as a list. Also i have not figured out how to handle the keyword argument.

Also, i am still stuck at the augassignOp because i cannot use a lambda expression like l'ambda a, b: a = a + b' as shown in the airth.py example.

Would appreciate any feedback. Thanks.
#### 2017-09-02 08:47:24 - ptmcg
The parsed data returned by pyparsing implements all the methods of a list so that it can be treated as a list (len, for i in result, result[0], etc.). If you *must* have a list (for JSON serialization, for example), you can use result.asList() and the parsed data will be converted to a nested list. Note that this will strip any defined results names, like' fname' or 'argslist'.

augAssignOp won't really fit into into the infixNotation model because '+=' isn't really an operator. You can't write 'x * (a += 14)'. The '+=' can only occur as part of an enhanced assignment statement. So you should really implement '+=' as another form of assignment: 



    EQ = Literal('=')
    PLUS_EQ = Literal('+=')
    assignmentExpr = varname('lhs') + EQ('operator') + arithExpr('rhs')
    augmentedAssignmentExpr = varname('lhs') + PLUS_EQ('operator') + arithExpr('rhs')


and then have your overall parser match for 'assignment | augmentedAssignment'.



    statement_parser = assignmentExpr | augmentedAssignemtExpr


You could attach a parse action to statement_parser that would look at the variable name in 'lhs', the value in 'rhs', and the assignment or augmented assignment based on whether 'operator' was '=' or '+='.
#### 2017-09-03 04:59:49 - vacaut
Thanks for the clarification. Would you mind to give a simple example on how to assign the token value on rhs to variable on lhs? I tried something like this:


    assignmentExpr = Group(varname('lhs') + EQ('operator') + expr('rhs'))('assignment').addParseAction(lambda t: t[0] = t[-1])

but i got an error


    SyntaxError: lambda cannot contain assignment


Also, what is the difference between addParseAction and setParseAction?
#### 2017-09-03 06:12:07 - vacaut
ah, i did not notice the tokens become a list if i use Group function. After removing the Group and use code like this, i got


    def assignVar(t):
        global vars_
        vars_=defaultdict(float)
        print('t0 is {}'.format(t[0]))
        vars_[t[0]]=t[-1]

The var on lhs is updated with rhs value. If there is any better way, please let me know.
Another question is on the funccall. I would need to map many user function to python function. In the excelExpr.py example the funcCall is actually an aggregation using MatchFirst of various functions. This seems a bit tedious as we need to a new line each time we have a new function and then append the new function name in the funcCall line. Is there easier way such as just using a dictionary?
Sorry for all these many questions but i am glad to be able to make some progress little by little.



