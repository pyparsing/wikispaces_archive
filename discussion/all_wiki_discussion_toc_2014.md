## Pyparsing Wikispaces Discussion - 2014

[Note: these entries are fairly old, and predate many new features of pyparsing,
and are predominantly coded using Python 2.
They are captured here for historical benefit, but may not contain
the most current practices or features. We will try to add editor
notes to entries to indicate when discussions have been 
overtaken by development events.]

[2014-01-18 08:23:58 - matthewbward - housenumber help with address parsing](all_wiki_discussion_toc_2014.md#2014-01-18-082358---matthewbward---housenumber-help-with-address-parsing)  
[2014-02-09 08:39:23 - D3f0 - Grammar with functions with one or many arguments](all_wiki_discussion_toc_2014.md#2014-02-09-083923---d3f0---grammar-with-functions-with-one-or-many-arguments)  
[2014-02-13 00:55:08 - JamesEMH - parse only lines starting with keyword](all_wiki_discussion_toc_2014.md#2014-02-13-005508---jamesemh---parse-only-lines-starting-with-keyword)  
[2014-02-18 05:47:30 - egabancho - Illegal nesting exception depending on order](all_wiki_discussion_toc_2014.md#2014-02-18-054730---egabancho---illegal-nesting-exception-depending-on-order)  
[2014-03-26 08:01:35 - palmer1979 - Deep Nesting until Breakdown : )](all_wiki_discussion_toc_2014.md#2014-03-26-080135---palmer1979---deep-nesting-until-breakdown--)  
[2014-04-04 14:32:45 - igre62 - setParseAction](all_wiki_discussion_toc_2014.md#2014-04-04-143245---igre62---setparseaction)  
[2014-04-10 13:21:49 - couplewavylines - SkipTo ignore method](all_wiki_discussion_toc_2014.md#2014-04-10-132149---couplewavylines---skipto-ignore-method)  
[2014-05-02 15:07:57 - dbotz - My Optional is not optional](all_wiki_discussion_toc_2014.md#2014-05-02-150757---dbotz---my-optional-is-not-optional)  
[2014-05-24 02:53:43 - PrabhuGurumurthy - Help using delimitedList](all_wiki_discussion_toc_2014.md#2014-05-24-025343---prabhugurumurthy---help-using-delimitedlist)  
[2014-07-02 02:55:59 - nunoplopes - infixNotation is very slow](all_wiki_discussion_toc_2014.md#2014-07-02-025559---nunoplopes---infixnotation-is-very-slow)  
[2014-07-13 22:09:19 - vrvilo - `MatchFirst` truncates named results (pyparsing)](all_wiki_discussion_toc_2014.md#2014-07-13-220919---vrvilo---matchfirst-truncates-named-results-pyparsing)
[2014-07-21 18:34:31 - tony_chu - Question on parseString Optional () terms](all_wiki_discussion_toc_2014.md#2014-07-21-183431---tony_chu---question-on-parsestring-optional--terms)  
[2014-07-25 02:43:13 - AndreWin - parsing class definiton on python](all_wiki_discussion_toc_2014.md#2014-07-25-024313---andrewin---parsing-class-definiton-on-python)  
[2014-08-07 05:10:45 - pank1 - Ignoring comments](all_wiki_discussion_toc_2014.md#2014-08-07-051045---pank1---ignoring-comments)  
[2014-08-07 10:45:19 - cyrfer - making objects from ParsedResults](all_wiki_discussion_toc_2014.md#2014-08-07-104519---cyrfer---making-objects-from-parsedresults)  
[2014-08-12 16:11:31 - rh0dium - Small problem with recurssion - I'm sooo close..](all_wiki_discussion_toc_2014.md#2014-08-12-161131---rh0dium---small-problem-with-recurssion---im-sooo-close)  
[2014-09-07 00:35:14 - AndreWin - Parsing units on Russian](all_wiki_discussion_toc_2014.md#2014-09-07-003514---andrewin---parsing-units-on-russian)  
[2014-09-18 00:41:16 - gustible - Multi-Line Parsing](all_wiki_discussion_toc_2014.md#2014-09-18-004116---gustible---multi-line-parsing)  
[2014-10-14 02:53:00 - cnayak12 - Need help on how to parse the repeated blocks of text to a nested dictionary](all_wiki_discussion_toc_2014.md#2014-10-14-025300---cnayak12---need-help-on-how-to-parse-the-repeated-blocks-of-text-to-a-nested-dictionary)  
[2014-11-17 13:23:32 - Griffon26 - error stop does not break out of Each](all_wiki_discussion_toc_2014.md#2014-11-17-132332---griffon26---error-stop-does-not-break-out-of-each)  
[2014-11-22 04:18:48 - Griffon26 - Trivial fix to increase usefulness of Each()'s error reporting](all_wiki_discussion_toc_2014.md#2014-11-22-041848---griffon26---trivial-fix-to-increase-usefulness-of-eachs-error-reporting)  
[2014-11-23 02:51:18 - dlxneamtu - OneOrMore issue](all_wiki_discussion_toc_2014.md#2014-11-23-025118---dlxneamtu---oneormore-issue)  
[2014-11-26 12:52:12 - Griffon26 - LineEnd() matches at StringEnd() as well. Should it?](all_wiki_discussion_toc_2014.md#2014-11-26-125212---griffon26---lineend-matches-at-stringend-as-well-should-it)  
[2014-12-06 09:14:40 - Griffon26 - Parsing within quotes?](all_wiki_discussion_toc_2014.md#2014-12-06-091440---griffon26---parsing-within-quotes)  
[2014-12-15 08:00:31 - vsvismeista - adding key\/value pair to originally ParseResults Object](all_wiki_discussion_toc_2014.md#2014-12-15-080031---vsvismeista---adding-key\value-pair-to-originally-parseresults-object)  
[2014-12-18 02:11:05 - perw07 - How best to traverse lists in pyparsing results?](all_wiki_discussion_toc_2014.md#2014-12-18-021105---perw07---how-best-to-traverse-lists-in-pyparsing-results)  


---
## 2014-01-18 08:23:58 - matthewbward - housenumber help with address parsing
hey guys,

i'm new to pyparsing and am having trouble modifying the address parser to fit an additional need.  while the parser detects an address like 41-A correctly as a housenumber, and i can modify the code to accept 41-1 (changing alphas to alphanums), i can't figure out how to make the address parser interpret 41-133 as a valid house number.  that address format is fairly common in hawaii. 

thanks!

-matt

#### 2014-01-18 08:38:05 - ptmcg
Try changing the housenumberexpression from:

    housenumber = originalTextFor( numberword | Combine(Word(nums) + 
                        Optional(OPT_DASH + oneOf(list(alphas))+FollowedBy(White()))) + 
                        Optional(OPT_DASH + '1/2')

to

    housenumber = originalTextFor( numberword | Combine(Word(nums) + 
                        Optional(OPT_DASH + (Word(nums) | oneOf(list(alphas)))+FollowedBy(White()))) + 
                        Optional(OPT_DASH + '1/2')

-- Paul
#### 2014-01-18 17:10:15 - matthewbward
thank you very much! that's what i needed.

---
## 2014-02-09 08:39:23 - D3f0 - Grammar with functions with one or many arguments
Hi!
I've been modifying PyParsing examples to try to implement a simple DSL for calculations.
It consists of numeric literals, vairables (which have a specific format i.e.: ai.V0000.attribute). It has some type casts very similiar to python's int(), str() and float(). Logic operations wich accepts variable arguments (AND, OR). It also has simple arithmetics (+,-,* and /). Finally it has comparision with an IF function (condition, if_true, if_false).

I started to implement it modifying excel's formula example provided with pyparsing. But I struggled with reucurssion:

    from pyparsing import *
    
    # Variables
    variable = Regex(r'(?P<table>[ai|di|sv]{2})\.(?P<tag>[\w\d]+)\.(?P<attr>\w+)')
    
    
    def var_parse_action(text, index, context):
        return context[0]
    
    variable.setParseAction(var_parse_action)
    
    # Numbers
    numeric_literal = Regex(r'\-?\d+(\.\d+)?')
    
    
    def number_prase_action(text, index, data):
        number = data[0]
        if '.' in number:
            return float(number)
        else:
            return int(number)
    
    numeric_literal.setParseAction(number_prase_action)
    
    EXCL, LPAR, RPAR, COLON, COMMA = map(Suppress, '!():,')
    
    expr = Forward()
    
    # IF CONDITION
    COMPARISON_OP = oneOf('< = > >= <= != <>')
    condExpr = (expr + COMPARISON_OP + expr) | variable
    
    ifFunc = (CaselessKeyword('si') +
              LPAR +
              Group(condExpr)('condition') +
              COMMA + expr('if_true') +
              COMMA + expr('if_false') + RPAR)
    
    #def ifFunc_parse_action(text, index, context):
    # print 'hola'
    return context</li></ol>#
    #ifFunc.setParseAction(ifFunc_parse_action)
    
    arguments = Forward()
    
    one_op_func = lambda name: (CaselessKeyword(name) + LPAR + arguments + RPAR)
    
    int_cast = one_op_func('int')
    
    def int_cast_parse_action(text, index, context):
        return int(context[1])
    
    int_cast.setParseAction(int_cast_parse_action)
    float_cast = one_op_func('float')
    str_cast = one_op_func('str')
    
    sqrt_func = one_op_func('raiz')
    
    
    multi_op_func = lambda name: CaselessKeyword(name) + LPAR + delimitedList(arguments) + RPAR
    
    # Statistical functions
    sumFunc = multi_op_func('sum')
    minFunc = multi_op_func('min')
    maxFunc = multi_op_func('max')
    aveFunc = multi_op_func('ave')
    
    # Logical functions
    orFunc = multi_op_func('or')
    andFunc = multi_op_func('and')
    
    multOp = oneOf('* /')
    addOp = oneOf('+ -')
    
    
    funcCall = (ifFunc | # If expression
                sumFunc | minFunc | maxFunc | aveFunc | # statisticial functions
                int_cast | str_cast | float_cast | # Casts
                orFunc | andFunc | # Logical
                sqrt_func
                )
    
    arguments << (Group(expr) | numeric_literal | variable)
    
    
    operand = Forward()
    arithExpr = operatorPrecedence(operand,[
                                            (multOp, 2, opAssoc.LEFT),
                                            (addOp, 2, opAssoc.LEFT),
                                   ])
    
    operand << (arithExpr | numeric_literal  | variable)
    
    def arithExpr_parse_action(text, index, context):
        print 'ARIEXPR', context
    
    expr << (arithExpr | funcCall | numeric_literal | variable )
    

The test code is like this:

    test_line('int(3)+int(4)')
    test_line('or(0,1,2)')
    test_line('str(aa.bb.cc)')
    test_line('str(si(0>2,aa.bb.cc,4))')
    test_line('RAIZ(ai.E42PA_01.value*ai.E42PA_01.value+ai.E42PR_01.value*ai.E42PR_01.value)*ai.E42PA_01.escala')
    test_line('str(raiz(3)*2)')
    test_line('str(RAIZ(ai.E42PA_01.value*ai.E42PA_01.value+ai.E42PR_01.value*ai.E42PR_01.value)*ai.E42PA_01.escala)')

Thanks!

#### 2014-02-09 08:48:13 - D3f0
The code is attached here for easier reading: 

---
## 2014-02-13 00:55:08 - JamesEMH - parse only lines starting with keyword
Hello,
I am trying to parse a block of text lines where the lines of interest always begin with a keyword from a set of known keywords. All other lines can be ignored, even if they contain the keyword which is not the first entry in that line.
The code that follows almost works but stops when it meets an unwanted line containing one of the known keywords ('kw1' and 'kw2').


    def main():
        # A test string where I want to match all lines starting with
        # a keyword 'kw1' or 'kw2'.
        # Other lines should not be matched.
        test_string_1 = '''
                        An unwanted line can contain anything
                        kw2 par1
                        kw1 par1 2
                        another unwanted line
                        kw1 opt 1
                        another unwanted line that contains a kw1
                        kw2 h1
                        yet another unwanted line
        kw1 = Literal('kw1')
        kw2 = Literal('kw2')
        keywords = (kw1 | kw2)
        kw1_record = (kw1 +  Word(alphanums) + Word(nums) +
                        restOfLine.suppress() + LineEnd().suppress())
        kw2_record = (kw2 + Word(alphanums) +
                        restOfLine.suppress() + LineEnd().suppress())
        valid_records = (kw1_record | kw2_record)
        record = Group(SkipTo(keywords, include=False,
                              ignore=None, failOn=None).suppress() +
                          valid_records)
    
        all_records = ZeroOrMore(record)
    
        res = all_records.parseString(test_string_1)
        for entry in res:
            print entry
    
    if __name__ == '__main__':
        main()


The output from this code is 

    ['kw2', 'par1']
    ['kw1', 'par1', '2']
    ['kw1', 'opt', '1']

What is missing from the output is

    ['kw2', 'h1']

I am new to pyparsing and so I am probably missing something obvious. Is there a way to correct my code so that it does what I want? Or is there a better way to achieve my aims?

I would be grateful for any suggestions.

Thanks in advance,
James


---
## 2014-02-18 05:47:30 - egabancho - Illegal nesting exception depending on order
Illegal nesting exception depending on the order

Hi I'm trying to parse files like this one:



    '''
    Test model
    '''
    
    fields:
        @inherit_from(('base', ))
        abstract
        authors
        keywords
        title_article=title
    
    extensions:
        invenio.modules.jsonalchemy.testsuite.test_parser:DummyExtension
        invenio.modules.jsonalchemy.testsuite.test_parser:DummyExtension


for that I have the following python code:



    indent_stack = [1]
    
    field_def = (Word(alphas + '_', alphanums + '_') + \
                 Optional(Suppress('=') + \
                 Word(alphas + '_', alphanums + '_')))\
                 .setResultsName('field_definition', listAllMatches=True)
    inherit_from = (Suppress('@inherit_from') + \
                    originalTextFor(nestedExpr('(', ')')))\
                   .setResultsName('inherit_from')
    
    fields_body = Optional(inherit_from) + OneOrMore(field_def)
    
    fields = (Keyword('fields:').suppress() + \
              indentedBlock(fields_body, indent_stack))\
             .setResultsName('fields')
    comment = (Literal('#') + restOfLine + LineEnd()).suppress()
    
    return OneOrMore(comment) & Each([Optional(fields), ] + \
                [Optional(p.parser.parse_element(indent_stack))
                    for p in parsers \
                        if issubclass(p.parser, ModelBaseExtensionParser)])
    


And the parsers inside the for loop at the end are basically extensions for the main parser like this:



    class ExtensionModelParser(ModelBaseExtensionParser):
        __parsername__ = 'extensions'
    
        @classmethod
        def parse_element(cls, indent_stack):
            '''Sets ``extensions`` attribute to the rule definition'''
            extensions = indentedBlock(Word(alphanums + '_' + '.' + ':'),
                                       indent_stack)
    
            return (Keyword('extensions:') + OneOrMore(extensions))\
                    .setResultsName('extensions')


My problem is that I'm getting illegal nesting exceptions depending on the order, i.e. if I swich extensions and fields from the example file at the begining it will work.

I would really appreciate a bit of help here :)

Thanks,
Esteban


---
## 2014-03-26 08:01:35 - palmer1979 - Deep Nesting until Breakdown : )
Hello,

I have to parse a deeply nested expression. The parsing works for nesting up to 5 levels. 
When I have more levels, pyparsing seems to go into an infinite loop. I let the parser 
run for 12 hours, but to no avail. Is there any way around this?

What I also find strange is, that there seems to be no increased memory usage, which I 
would associate with infinite loops.

The grammar and the schema-string that need to be parsed are all in the code below. 
The code 'snippet' will run (forever) on any python that has the pyparsing package installed. 
I have tested it on thousands of lines of code and it works fine, except for deeply 
nested expressions.

By the way, you can just look at the last 30 lines of the code, and especially the 
recursive 'simple_factor << ...' expression, as these are where 'its happening'.

Any hint on how I might resolve this would be greatly appreciated!

Best regards,
Arne



    from pyparsing import *
    import pprint
    
    
    keywords = []
    
    ABS = CaselessKeyword('abs')
    keywords.append('ABS')
    
    ABSTRACT = CaselessKeyword('abstract')
    keywords.append('ABSTRACT')
    
    ACOS = CaselessKeyword('acos')
    keywords.append('ACOS')
    
    AGGREGATE = CaselessKeyword('aggregate')
    keywords.append('AGGREGATE')
    
    ALIAS = CaselessKeyword('alias')
    keywords.append('ALIAS')
    
    AND = CaselessKeyword('and')
    keywords.append('AND')
    
    ANDOR = CaselessKeyword('andor')
    keywords.append('ANDOR')
    
    ARRAY = CaselessKeyword('array')
    keywords.append('ARRAY')
    
    AS = CaselessKeyword('as')
    keywords.append('AS')
    
    ASIN = CaselessKeyword('asin')
    keywords.append('ASIN')
    
    ATAN = CaselessKeyword('atan')
    keywords.append('ATAN')
    
    BAG = CaselessKeyword('bag')
    keywords.append('BAG')
    
    BASED_ON = CaselessKeyword('based_on')
    keywords.append('BASED_ON')
    
    BEGIN = CaselessKeyword('begin')
    keywords.append('BEGIN')
    
    BINARY = CaselessKeyword('binary')
    keywords.append('BINARY')
    
    BLENGTH = CaselessKeyword('blength')
    keywords.append('BLENGTH')
    
    BOOLEAN = CaselessKeyword('boolean')
    keywords.append('BOOLEAN')
    
    BY = CaselessKeyword('by')
    keywords.append('BY')
    
    CASE = CaselessKeyword('case')
    keywords.append('CASE')
    
    CONSTANT = CaselessKeyword('constant')
    keywords.append('CONSTANT')
    
    CONST_E = CaselessKeyword('const_e')
    keywords.append('CONST_E')
    
    COS = CaselessKeyword('cos')
    keywords.append('COS')
    
    DERIVE = CaselessKeyword('derive')
    keywords.append('DERIVE')
    
    DIV = CaselessKeyword('div')
    keywords.append('DIV')
    
    ELSE = CaselessKeyword('else')
    keywords.append('ELSE')
    
    END = CaselessKeyword('end')
    keywords.append('END')
    
    END_ALIAS = CaselessKeyword('end_alias')
    keywords.append('END_ALIAS')
    
    END_CASE = CaselessKeyword('end_case')
    keywords.append('END_CASE')
    
    END_CONSTANT = CaselessKeyword('end_constant')
    keywords.append('END_CONSTANT')
    
    END_ENTITY = CaselessKeyword('end_entity')
    keywords.append('END_ENTITY')
    
    END_FUNCTION = CaselessKeyword('end_function')
    keywords.append('END_FUNCTION')
    
    END_IF = CaselessKeyword('end_if')
    keywords.append('END_IF')
    
    END_LOCAL = CaselessKeyword('end_local')
    keywords.append('END_LOCAL')
    
    END_PROCEDURE = CaselessKeyword('end_procedure')
    keywords.append('END_PROCEDURE')
    
    END_REPEAT = CaselessKeyword('end_repeat')
    keywords.append('END_REPEAT')
    
    END_RULE = CaselessKeyword('end_rule')
    keywords.append('END_RULE')
    
    END_SCHEMA = CaselessKeyword('end_schema')
    keywords.append('END_SCHEMA')
    
    END_SUBTYPE_CONSTRAINT = CaselessKeyword('end_subtype_constraint')
    keywords.append('END_SUBTYPE_CONSTRAINT')
    
    END_TYPE = CaselessKeyword('end_type')
    keywords.append('END_TYPE')
    
    ENTITY = CaselessKeyword('entity')
    keywords.append('ENTITY')
    
    ENUMERATION = CaselessKeyword('enumeration')
    keywords.append('ENUMERATION')
    
    ESCAPE = CaselessKeyword('escape')
    keywords.append('ESCAPE')
    
    EXISTS = CaselessKeyword('exists')
    keywords.append('EXISTS')
    
    EXTENSIBLE = CaselessKeyword('extensible')
    keywords.append('EXTENSIBLE')
    
    EXP = CaselessKeyword('exp')
    keywords.append('EXP')
    
    FALSE = CaselessKeyword('false')
    keywords.append('FALSE')
    
    FIXED = CaselessKeyword('fixed')
    keywords.append('FIXED')
    
    FOR = CaselessKeyword('for')
    keywords.append('FOR')
    
    FORMAT = CaselessKeyword('format')
    keywords.append('FORMAT')
    
    FROM = CaselessKeyword('from')
    keywords.append('FROM')
    
    FUNCTION = CaselessKeyword('function')
    keywords.append('FUNCTION')
    
    GENERIC = CaselessKeyword('generic')
    keywords.append('GENERIC')
    
    GENERIC_ENTITY = CaselessKeyword('generic_entity')
    keywords.append('GENERIC_ENTITY')
    
    HIBOUND = CaselessKeyword('hibound')
    keywords.append('HIBOUND')
    
    HIINDEX = CaselessKeyword('hiindex')
    keywords.append('HIINDEX')
    
    IF = CaselessKeyword('if')
    keywords.append('IF')
    
    IN = CaselessKeyword('in')
    keywords.append('IN')
    
    INSERT = CaselessKeyword('insert')
    keywords.append('INSERT')
    
    INTEGER = CaselessKeyword('integer')
    keywords.append('INTEGER')
    
    INVERSE = CaselessKeyword('inverse')
    keywords.append('INVERSE')
    
    LENGTH = CaselessKeyword('length')
    keywords.append('LENGTH')
    
    LIKE = CaselessKeyword('like')
    keywords.append('LIKE')
    
    LIST = CaselessKeyword('list')
    keywords.append('LIST')
    
    LOBOUND = CaselessKeyword('lobound')
    keywords.append('LOBOUND')
    
    LOCAL = CaselessKeyword('local')
    keywords.append('LOCAL')
    
    LOG = CaselessKeyword('log')
    keywords.append('LOG')
    
    LOG10 = CaselessKeyword('log10')
    keywords.append('LOG10')
    
    LOG2 = CaselessKeyword('log2')
    keywords.append('LOG2')
    
    LOGICAL = CaselessKeyword('logical')
    keywords.append('LOGICAL')
    
    LOINDEX = CaselessKeyword('loindex')
    keywords.append('LOINDEX')
    
    MOD = CaselessKeyword('mod')
    keywords.append('MOD')
    
    NOT = CaselessKeyword('not')
    keywords.append('NOT')
    
    NUMBER = CaselessKeyword('number')
    keywords.append('NUMBER')
    
    NVL = CaselessKeyword('nvl')
    keywords.append('NVL')
    
    ODD = CaselessKeyword('odd')
    keywords.append('ODD')
    
    OF = CaselessKeyword('of')
    keywords.append('OF')
    
    ONEOF = CaselessKeyword('oneof')
    keywords.append('ONEOF')
    
    OPTIONAL = CaselessKeyword('optional')
    keywords.append('OPTIONAL')
    
    OR = CaselessKeyword('or')
    keywords.append('OR')
    
    OTHERWISE = CaselessKeyword('otherwise')
    keywords.append('OTHERWISE')
    
    PI = CaselessKeyword('pi')
    keywords.append('PI')
    
    PROCEDURE = CaselessKeyword('procedure')
    keywords.append('PROCEDURE')
    
    QUERY = CaselessKeyword('query')
    keywords.append('QUERY')
    
    REAL = CaselessKeyword('real')
    keywords.append('REAL')
    
    REFERENCE = CaselessKeyword('reference')
    keywords.append('REFERENCE')
    
    REMOVE = CaselessKeyword('remove')
    keywords.append('REMOVE')
    
    RENAMED = CaselessKeyword('renamed')
    keywords.append('RENAMED')
    
    REPEAT = CaselessKeyword('repeat')
    keywords.append('REPEAT')
    
    RETURN = CaselessKeyword('return')
    keywords.append('RETURN')
    
    ROLESOF = CaselessKeyword('rolesof')
    keywords.append('ROLESOF')
    
    RULE = CaselessKeyword('rule')
    keywords.append('RULE')
    
    SCHEMA = CaselessKeyword('schema')
    keywords.append('SCHEMA')
    
    SELECT = CaselessKeyword('select')
    keywords.append('SELECT')
    
    SELF = CaselessKeyword('self')
    keywords.append('SELF')
    
    SET = CaselessKeyword('set')
    keywords.append('SET')
    
    SIN = CaselessKeyword('sin')
    keywords.append('SIN')
    
    SIZEOF = CaselessKeyword('sizeof')
    keywords.append('SIZEOF')
    
    SKIP = CaselessKeyword('skip')
    keywords.append('SKIP')
    
    SQRT = CaselessKeyword('sqrt')
    keywords.append('SQRT')
    
    STRING = CaselessKeyword('string')
    keywords.append('STRING')
    
    SUBTYPE = CaselessKeyword('subtype')
    keywords.append('SUBTYPE')
    
    SUBTYPE_CONSTRAINT = CaselessKeyword('subtype_constraint')
    keywords.append('SUBTYPE_CONSTRAINT')
    
    SUPERTYPE = CaselessKeyword('supertype')
    keywords.append('SUPERTYPE')
    
    TAN = CaselessKeyword('tan')
    keywords.append('TAN')
    
    THEN = CaselessKeyword('then')
    keywords.append('THEN')
    
    TO = CaselessKeyword('to')
    keywords.append('TO')
    
    TOTAL_OVER = CaselessKeyword('total_over')
    keywords.append('TOTAL_OVER')
    
    TRUE = CaselessKeyword('true')
    keywords.append('TRUE')
    
    TYPE = CaselessKeyword('type')
    keywords.append('TYPE')
    
    TYPEOF = CaselessKeyword('typeof')
    keywords.append('TYPEOF')
    
    UNIQUE = CaselessKeyword('unique')
    keywords.append('UNIQUE')
    
    UNKNOWN = CaselessKeyword('unknown')
    keywords.append('UNKNOWN')
    
    UNTIL = CaselessKeyword('until')
    keywords.append('UNTIL')
    
    USE = CaselessKeyword('use')
    keywords.append('USE')
    
    USEDIN = CaselessKeyword('usedin')
    keywords.append('USEDIN')
    
    VALUE = CaselessKeyword('value')
    keywords.append('VALUE')
    
    VALUE_IN = CaselessKeyword('value_in')
    keywords.append('VALUE_IN')
    
    VALUE_UNIQUE = CaselessKeyword('value_unique')
    keywords.append('VALUE_UNIQUE')
    
    VAR = CaselessKeyword('var')
    keywords.append('VAR')
    
    WHERE = CaselessKeyword('where')
    keywords.append('WHERE')
    
    WHILE = CaselessKeyword('while')
    keywords.append('WHILE')
    
    WITH = CaselessKeyword('with')
    keywords.append('WITH')
    
    XOR = CaselessKeyword('xor')
    keywords.append('XOR')
    
    bit = oneOf('0 1')
    
    digit = oneOf(list(nums))
    
    digits = OneOrMore(digit)
    
    hex_digit = oneOf(list(hexnums))
    
    letter = oneOf(list(alphas))
    
    octet = hex_digit + hex_digit
    
    encoded_character = octet + octet + octet + octet
    
    not_paren_star_quote_special = oneOf(r'! ' # $ % & + , - . / : ; < = > ? @ [ \ ] ^ _ { | } ~')
    
    not_paren_star_special = not_paren_star_quote_special | ''''
    
    not_paren_star = letter | digit | not_paren_star_special
    
    not_lparen_star = not_paren_star | ')'
    
    lparen_then_not_lparen_star = '(' + ZeroOrMore('(') + OneOrMore(not_lparen_star)
    
    not_quote = not_paren_star_quote_special | letter | digit | '(' | ')' | '*'
    
    not_rparen_star = not_paren_star | '('
    
    special = not_paren_star_quote_special | '(' | ')' | '*' | ''''
    
    not_rparen_star_then_rparen = OneOrMore(not_rparen_star) + OneOrMore(')')
    
    sign = oneOf('+ -')
    
    binary_literal = Group(Combine('%' + OneOrMore(bit)))
    
    encoded_string_literal = Group(Combine(''' + OneOrMore(encoded_character) + '''))
    
    integer_literal = Group(digits)
    
    real_literal = Group(Combine(integer_literal ^ ( digits + '.' + Optional(digits) + \
                                                     Optional(CaselessKeyword('e') + Optional(sign) + digits))))
    
    simple_id = NotAny(oneOf(keywords, caseless=True) + (WordEnd(alphanums + '_') | White())) + \
                Group(Combine(letter + ZeroOrMore(letter | digit | '_')))
    
    simple_string_literal = Group(Combine(''' + ZeroOrMore('''' | not_quote | ' ' | u'\u0009' | u'\u000A' | u'\u000D') \
                                          + '''))
    
    attribute_id = simple_id
    
    attribute_ref = attribute_id
    
    constant_id = simple_id
    
    constant_ref = constant_id
    
    entity_id = simple_id
    
    entity_ref = entity_id
    
    enumeration_id = simple_id
    
    enumeration_ref = enumeration_id
    
    function_id = simple_id
    
    function_ref = function_id
    
    parameter_id = simple_id
    
    parameter_ref = parameter_id
    
    procedure_id = simple_id
    
    procedure_ref = procedure_id
    
    rule_label_id = simple_id
    
    rule_label_ref = rule_label_id
    
    rule_id = simple_id
    
    rule_ref = rule_id
    
    schema_id = simple_id
    
    schema_ref = schema_id
    
    subtype_constraint_id = simple_id
    
    subtype_constraint_ref = subtype_constraint_id
    
    type_label_id = simple_id
    
    type_label_ref = type_label_id
    
    type_id = simple_id
    
    type_ref = type_id
    
    variable_id = simple_id
    
    variable_ref = variable_id
    
    remark_ref = attribute_ref | constant_ref | entity_ref | enumeration_ref | function_ref | parameter_ref | procedure_ref | rule_label_ref | rule_ref | schema_ref | subtype_constraint_ref | type_label_ref | type_ref | variable_ref
    
    remark_tag = ''' + remark_ref + ZeroOrMore('.' + remark_ref) + '''
    
    embedded_remark = Keyword('(*') + Optional(remark_tag) + ZeroOrMore(NotAny(Keyword('*)')) + Word(printables)) + \
                      Keyword('*)')
    
    tail_remark = Literal('--') + Optional(remark_tag) + ZeroOrMore(NotAny(LineEnd()) + Word(printables)) + LineEnd()
    
    remark = embedded_remark | tail_remark
    
    abstract_entity_declaration = ABSTRACT
    
    abstract_supertype = ABSTRACT + SUPERTYPE + ';'
    
    add_like_op = Literal('+') | Literal('-') | OR | XOR
    
    multiplication_like_op = Literal('*') | Literal('/') | Literal('||') | DIV | MOD | AND
    
    unary_op = Literal('+') | Literal('-') | NOT
    
    attribute_qualifier = '.' + attribute_ref
    
    boolean_type = BOOLEAN
    
    built_in_constant = CONST_E | PI | SELF | Literal('?')
    
    built_in_function = ABS | ACOS | ASIN | ATAN | BLENGTH | COS | EXISTS | EXP | FORMAT | HIBOUND | HIINDEX | LENGTH | LOBOUND | LOINDEX | LOG | LOG2 | LOG10 | NVL | ODD | ROLESOF | SIN | SIZEOF | SQRT | TAN | TYPEOF | USEDIN | VALUE | VALUE_IN | VALUE_UNIQUE
    
    built_in_procedure = INSERT | REMOVE
    
    enumeration_items = '(' + delimitedList(enumeration_id) + ')'
    
    escape_stmt = ESCAPE + ';'
    
    type_label = type_label_id | type_label_ref
    
    generic_entity_type = GENERIC_ENTITY + Optional(':' + type_label)
    
    generic_type = GENERIC + Optional(':' + type_label)
    
    integer_type = INTEGER
    
    interval_op = oneOf('< <=')
    
    logical_literal = FALSE | TRUE | UNKNOWN
    
    logical_type = LOGICAL
    
    null_stmt = Literal(';')
    
    number_type = NUMBER
    
    rel_op = oneOf('< > <= >= <> = :<>: :=:')
    
    rel_op_extended = rel_op | IN | LIKE
    
    rename_id = constant_id | entity_id | function_id | procedure_id | type_id
    
    resource_ref = constant_ref | entity_ref | function_ref | procedure_ref | type_ref
    
    resource_or_rename = resource_ref + Optional(AS + rename_id)
    
    string_literal = simple_string_literal | encoded_string_literal
    
    schema_version_id = string_literal
    
    named_types = entity_ref | type_ref
    
    named_type_or_rename = named_types + Optional(AS + ( entity_id | type_id ))
    
    population = entity_ref
    
    general_ref = parameter_ref | variable_ref
    
    literal = binary_literal | logical_literal | real_literal | string_literal
    
    group_qualifier = '\\' + entity_ref
    
    select_list = '(' + delimitedList(named_types) + ')'
    
    select_extension = BASED_ON + type_ref + Optional(WITH + select_list)
    
    select_type = Optional(EXTENSIBLE + Optional(GENERIC_ENTITY)) + SELECT + Optional(select_list | select_extension)
    
    skip_stmt = SKIP + ';'
    
    total_over = TOTAL_OVER + '(' + delimitedList(entity_ref) + ')' + ';'
    
    reference_clause = REFERENCE + FROM + schema_ref + Optional('(' + delimitedList(resource_or_rename) + ')') + ';'
    
    use_clause = USE + FROM + schema_ref + Optional('(' + delimitedList(named_type_or_rename) + ')') + ';'
    
    interface_specification = reference_clause | use_clause
    
    subtype_constraint_head = SUBTYPE_CONSTRAINT + subtype_constraint_id + FOR + entity_ref + ';'
    
    subtype_declaration = SUBTYPE + OF + '(' + delimitedList(entity_ref) + ')'
    
    rule_head = RULE + rule_id + FOR + '(' + delimitedList(entity_ref) + ')' + ';'
    
    qualified_attribute = SELF + group_qualifier + attribute_qualifier
    
    referenced_attribute = attribute_ref | qualified_attribute
    
    redeclared_attribute = qualified_attribute + Optional(RENAMED + attribute_id)
    
    enumeration_extension = BASED_ON + type_ref + Optional(WITH + enumeration_items)
    
    enumeration_reference = Optional(type_ref + '.') + enumeration_ref
    
    enumeration_type = Optional(EXTENSIBLE) + ENUMERATION + Optional(( OF + enumeration_items ) ^ enumeration_extension)
    
    constructed_types = enumeration_type | select_type
    
    constant_factor = built_in_constant | constant_ref
    
    attribute_decl = attribute_id | redeclared_attribute
    
    unique_rule = Optional(rule_label_id + ':') + delimitedList(referenced_attribute)
    
    simple_factor = Forward()
    
    factor = simple_factor + Optional('**' + simple_factor)
    
    term = factor + ZeroOrMore(multiplication_like_op + factor)
    
    simple_expression = term + ZeroOrMore(add_like_op + term)
    
    expression = simple_expression + Optional(rel_op_extended + simple_expression)
    
    interval_high = simple_expression
    
    interval_item = simple_expression
    
    interval_low = simple_expression
    
    interval = '{' + interval_low + interval_op + interval_item + interval_op + interval_high + '}'
    
    numeric_expression = simple_expression
    
    repetition = numeric_expression
    
    element = expression + Optional(':' + repetition)
    
    aggregate_initializer = '[' + Optional(delimitedList(element)) + ']'
    
    logical_expression = expression
    
    aggregate_source = simple_expression
    
    query_expression = QUERY + '(' + variable_id + '<*' + aggregate_source + '|' + logical_expression + ')'
    
    index = numeric_expression
    
    index_1 = index
    
    index_2 = index
    
    index_qualifier = '[' + index_1 + Optional(':' + index_2) + ']'
    
    qualifier = attribute_qualifier | group_qualifier | index_qualifier
    
    parameter = expression
    
    actual_parameter_list = '(' + delimitedList(parameter) + ')'
    
    function_call = ( built_in_function | function_ref ) + Optional(actual_parameter_list)
    
    qualifiable_factor = attribute_ref ^ constant_factor ^ function_call ^ general_ref ^ population
    
    primary = literal | ( qualifiable_factor + ZeroOrMore(qualifier) )
    
    entity_constructor = entity_ref + '(' + Optional(delimitedList(expression)) + ')'
    
    simple_factor << (aggregate_initializer ^ entity_constructor ^ enumeration_reference ^ interval ^ query_expression ^ \
                      (Optional(unary_op) + ( ('(' + expression + ')') ^ primary ) ))
    
    schema = '''
    (
     (
      (
       (
        (
         (
          (
           (
            (
             (
              EXISTS(internal_location) OR EXISTS(street_number)
             ) OR EXISTS(street)
            ) OR EXISTS(postal_box)
           ) OR EXISTS(town)
          ) OR EXISTS(region)
         ) OR EXISTS(postal_code)
        ) OR EXISTS(country)
       ) OR EXISTS(facsimile_number)
      ) OR EXISTS(telephone_number)
     ) OR EXISTS(electronic_mail_address)
    ) OR EXISTS(telex_number);
    
    '''
    
    data = expression.parseString(schema)
    pp = pprint.PrettyPrinter(indent=4)
    pp.pprint(data.asList())

#### 2014-03-27 08:51:08 - palmer1979
Hi, I managed to get tweak this so that it works now. No reply required.
#### 2014-03-27 10:30:59 - ptmcg
I'm glad you got this worked out for yourself.  I did a little work with your program, one thing that will make it a little more manageable was that I collapsed the large keyword section down to this:


    keywords = []
    
    def makeCaselessKeyword(s):
        ret = CaselessKeyword(s)
        keywords.append(s)
        return ret
    
    (ABS, ABSTRACT, ACOS, AGGREGATE, ALIAS, AND, ANDOR, ARRAY, AS, ASIN,
    ATAN, BAG, BASED_ON, BEGIN, BINARY, BLENGTH, BOOLEAN, BY, CASE,
    CONSTANT, CONST_E, COS, DERIVE, DIV, ELSE, END, END_ALIAS, END_CASE,
    END_CONSTANT, END_ENTITY, END_FUNCTION, END_IF, END_LOCAL,
    END_PROCEDURE, END_REPEAT, END_RULE, END_SCHEMA,
    END_SUBTYPE_CONSTRAINT, END_TYPE, ENTITY, ENUMERATION, ESCAPE, EXISTS,
    EXTENSIBLE, EXP, FALSE, FIXED, FOR, FORMAT, FROM, FUNCTION, GENERIC,
    GENERIC_ENTITY, HIBOUND, HIINDEX, IF, IN, INSERT, INTEGER, INVERSE,
    LENGTH, LIKE, LIST, LOBOUND, LOCAL, LOG, LOG10, LOG2, LOGICAL,
    LOINDEX, MOD, NOT, NUMBER, NVL, ODD, OF, ONEOF, OPTIONAL, OR,
    OTHERWISE, PI, PROCEDURE, QUERY, REAL, REFERENCE, REMOVE, RENAMED,
    REPEAT, RETURN, ROLESOF, RULE, SCHEMA, SELECT, SELF, SET, SIN, SIZEOF,
    SKIP, SQRT, STRING, SUBTYPE, SUBTYPE_CONSTRAINT, SUPERTYPE, TAN, THEN,
    TO, TOTAL_OVER, TRUE, TYPE, TYPEOF, UNIQUE, UNKNOWN, UNTIL, USE,
    USEDIN, VALUE, VALUE_IN, VALUE_UNIQUE, VAR, WHERE, WHILE, WITH, XOR) = \
    map(makeCaselessKeyword,
    '''abs abstract acos aggregate alias and andor array as asin atan bag
    based_on begin binary blength boolean by case constant const_e cos
    derive div else end end_alias end_case end_constant end_entity
    end_function end_if end_local end_procedure end_repeat end_rule
    end_schema end_subtype_constraint end_type entity enumeration escape
    exists extensible exp false fixed for format from function generic
    generic_entity hibound hiindex if in insert integer inverse length
    like list lobound local log log10 log2 logical loindex mod not number
    nvl odd of oneof optional or otherwise pi procedure query real
    reference remove renamed repeat return rolesof rule schema select self
    set sin sizeof skip sqrt string subtype subtype_constraint supertype
    tan then to total_over true type typeof unique unknown until use
    usedin value value_in value_unique var where while with xor'''.split())


ALso, you are blurring some of the concepts from regex with pyparsing, and forgetting that pyparsing includes implicit whitespace skipping. For instance, by defining digits as OneOrMore(digit), this will match not only '123', but also '1 2 3'. Is that your intention? You may need to rethink how this 
BNF->pyparsing definition should be defined.

-- Paul

---
## 2014-04-04 14:32:45 - igre62 - setParseAction
The following code



    def defA(toks):
        print 'defA'
    
    def defB(toks):
        print 'defB'
    
    aWord = Word('A')
    bWord = Word('B')
    
    Longer = ( aWord + bWord ).setParseAction( defA )
    Shorter = aWord.setParseAction( defB )
    
    print Longer.parseString( 'A B' )


executes both functions defA and defB.  This is perplexing.  I would expect only defA to be called.  What am I missing?

Ian

#### 2014-04-04 15:17:00 - adc2014
In the second last line, the parsAction for aWord was set to defB.  The fact that the result was assigned to Shorter doesn't matter.
#### 2014-04-04 16:07:45 - igre62
Ah, I begin to understand.  So what I would need to do is assign setParseAction to Longer and Shorter.  Like so:


    Longer = aWord + bWord
    Longer.setParseAction( defA )
    Shorter = aWord
    Shorter.setParseAction( defB )

But, it appears that in this example Shorter is a synonym for aWord.  To correct this I can add and Empty parser.  Like so:


    Longer = aWord + bWord
    Longer.setParseAction( defA )
    Shorter = aWord + Empty()
    Shorter.setParseAction( defB )

This appears to work.  Thanks for the help :-)
#### 2014-04-04 16:08:39 - igre62
Ah, I begin to understand.  So what I would need to do is assign setParseAction to Longer and Shorter.  Like so:


    Longer = aWord + bWord
    Longer.setParseAction( defA )
    Shorter = aWord
    Shorter.setParseAction( defB )

But, it appears that in this example Shorter is a synonym for aWord.  To correct this I can add and Empty parser.  Like so:


    Longer = aWord + bWord
    Longer.setParseAction( defA )
    Shorter = aWord + Empty()
    Shorter.setParseAction( defB )

This appears to work.  Thanks for the help :-)
#### 2014-04-04 16:35:16 - adc2014
What you had had was tantamount to

    Longer = ( aWord.setParseAction(defB) + bWord ).setParseAction(defA)

---
## 2014-04-10 13:21:49 - couplewavylines - SkipTo ignore method
Though I'm aware of the SkipTo constructor's 'ignore' parameter, I was surprised that the ignore() method didn't work:



    from pyparsing import *
    
    text = 'abc def 1234 123'
    
    good_pattern = Word(alphas) + SkipTo('123', ignore=Literal('1234'))
    print('Expected output:')
    print(good_pattern.parseString(text))
    
    bad_pattern = Word(alphas) + SkipTo('123').ignore(Literal('1234'))
    print('Unexpected output:')
    print(bad_pattern.parseString(text))


Outputs this:


    Expected output:
    ['abc', 'def 1234 ']
    Unexpected output:
    ['abc', 'def ']


Tried Python 3.4.0 and 2.7.6.

Is this a bug?  Or am I misunderstanding the use of the ignore() method?

#### 2014-04-13 10:48:02 - ptmcg
ignore() is not specific to SkipTo, it is applicable to any ParserElement. You use it to define structures that you want the parser to skip over entirely. It is usually used to indicate comment expressions, so that in the source text, a comment could appear almost anywhere, and pyparsing will ignore it. Sorry for the confusion.

-- Paul

---
## 2014-05-02 15:07:57 - dbotz - My Optional is not optional
Hi.

I'm trying to parse some HTML and when I use 'Optional', it does not appear to be optional.

I was wondering if you could help me understand why my Optional statement is not working .

Here is my code:



    #!/usr/bin/python
    from pyparsing import *
    
    bible='''<p class='p'><span class='v0_1_24'><sup id='Gen.1.24' class='v0_1_24'>24</sup> Then God said: Let the earth bring forth every kind of living creature: tame animals, crawling things, and every kind of wild animal. And so it happened: </span><span class='v0_1_25'><sup id='Gen.1.25' class='v0_1_25'>25</sup>God made every kind of wild animal, every kind of tame animal, and every kind of thing that crawls on the ground. God saw that it was good. </span><span class='v0_1_26'><sup id='Gen.1.26' class='v0_1_26'>26</sup> Then God said: Let us make human beings in our image, after our likeness. Let them have dominion over the fish of the sea, the birds of the air, the tame animals, all the wild animals, and all the creatures that crawl on the earth.</span></p>
    <p class='q1'><span class='v0_1_27'><sup id='Gen.1.27' class='v0_1_27'>27</sup>God created mankind in his image;</span></p>
    <p class='q2'><span class='v0_1_27'>in the image of God he created them;</span></p>
    <p class='q2'><span class='v0_1_27'>male and female he created them.</span></p>
    <p class='m'><span class='v0_1_28'><sup id='Gen.1.28' class='v0_1_28'>28</sup>God blessed them and God said to them: Be fertile and multiply; fill the earth and subdue it. Have dominion over the fish of the sea, the birds of the air, and all the living things that crawl on the earth. </span><span class='v0_1_29'><sup id='Gen.1.29' class='v0_1_29'>29</sup> God also said: See, I give you every seed-bearing plant on all the earth and every tree that has seed-bearing fruit on it to be your food; </span><span class='v0_1_30'><sup id='Gen.1.30' class='v0_1_30'>30</sup>and to all the wild animals, all the birds of the air, and all the living creatures that crawl on the earth, I give all the green plants for food. And so it happened. </span><span class='v0_1_31'><sup id='Gen.1.31' class='v0_1_31'>31</sup>God looked at everything he had made, and found it very good. Evening came, and morning followed- the sixth day.</span></p>'''
    
    verseWord = Word(printables, excludeChars = '<>')
    verseNumber = Word(nums)
    
    supOpen, supClose = makeHTMLTags('sup')
    
    spanOpen, spanClose = makeHTMLTags('span')
    
    verseNum = SkipTo(supOpen, include = True) + verseNumber.setResultsName('vNum') + SkipTo(supClose, include = True)
    
    aVerse = Combine(OneOrMore(verseWord), joinString = ' ', adjacent = False).setResultsName('theVerse')
    
    try1 = spanOpen + verseNum + aVerse + spanClose
    
    try2 = spanOpen + aVerse + spanClose
    
    try3 = spanOpen + Optional(verseNum) + aVerse + spanClose
    
    print 'Print out only entries that include a verse number'
    for tokens, start, end in try1.scanString(bible):
        print '{' + str(tokens.vNum) + '} ' + tokens.theVerse
        print
    
    print '####################################################'
    print 'Print out only entries that do not have verse number'
    for tokens, start, end in try2.scanString(bible):
        print '{' + str(tokens.vNum) + '} ' + tokens.theVerse
        print
    
    print '##########################################################'
    print 'Why does this NOT print out complete verses like verse 27?'
    for tokens, start, end in try3.scanString(bible):
        print '{' + str(tokens.vNum) + '} ' + tokens.theVerse
        print



Here is what I get for output when I run it:



    Print out only entries that include a verse number
    {24} Then God said: Let the earth bring forth every kind of living creature: tame animals, crawling things, and every kind of wild animal. And so it happened:
    
    {25} God made every kind of wild animal, every kind of tame animal, and every kind of thing that crawls on the ground. God saw that it was good.
    
    {26} Then God said: Let us make human beings in our image, after our likeness. Let them have dominion over the fish of the sea, the birds of the air, the tame animals, all the wild animals, and all the creatures that crawl on the earth.
    
    {27} God created mankind in his image;
    
    {28} God blessed them and God said to them: Be fertile and multiply; fill the earth and subdue it. Have dominion over the fish of the sea, the birds of the air, and all the living things that crawl on the earth.
    
    {29} God also said: See, I give you every seed-bearing plant on all the earth and every tree that has seed-bearing fruit on it to be your food;
    
    {30} and to all the wild animals, all the birds of the air, and all the living creatures that crawl on the earth, I give all the green plants for food. And so it happened.
    
    {31} God looked at everything he had made, and found it very good. Evening came, and morning followed- the sixth day.
    
    ####################################################
    Print out only entries that do not have verse number
    {} in the image of God he created them;
    
    {} male and female he created them.
    
    ##########################################################
    Why does this NOT print out complete verses like verse 27?
    {24} Then God said: Let the earth bring forth every kind of living creature: tame animals, crawling things, and every kind of wild animal. And so it happened:
    
    {25} God made every kind of wild animal, every kind of tame animal, and every kind of thing that crawls on the ground. God saw that it was good.
    
    {26} Then God said: Let us make human beings in our image, after our likeness. Let them have dominion over the fish of the sea, the birds of the air, the tame animals, all the wild animals, and all the creatures that crawl on the earth.
    
    {27} God created mankind in his image;
    
    {28} God blessed them and God said to them: Be fertile and multiply; fill the earth and subdue it. Have dominion over the fish of the sea, the birds of the air, and all the living things that crawl on the earth.
    
    {29} God also said: See, I give you every seed-bearing plant on all the earth and every tree that has seed-bearing fruit on it to be your food;
    
    {30} and to all the wild animals, all the birds of the air, and all the living creatures that crawl on the earth, I give all the green plants for food. And so it happened.
    
    {31} God looked at everything he had made, and found it very good. Evening came, and morning followed- the sixth day.


I had expected 'try3' to display verse 27 like this:



    {27} God created mankind in his image;
    
    {} in the image of God he created them;
    
    {} male and female he created them.


Thanks for the help and the GREAT Python module!
Dan

#### 2014-05-09 06:48:43 - dbotz
Played around a little bit more and found a solution (and learned a bit more about Pyparsing):



    #!/usr/bin/python
    from pyparsing import *
    
    bible='''<p class='p'><span class='v0_1_24'><sup id='Gen.1.24' class='v0_1_24'>24</sup> Then God said: Let the earth bring forth every kind of living creature: tame animals, crawling things, and every kind of wild animal. And so it happened: </span><span class='v0_1_25'><sup id='Gen.1.25' class='v0_1_25'>25</sup>God made every kind of wild animal, every kind of tame animal, and every kind of thing that crawls on the ground. God saw that it was good. </span><span class='v0_1_26'><sup id='Gen.1.26' class='v0_1_26'>26</sup> Then God said: Let us make human beings in our image, after our likeness. Let them have dominion over the fish of the sea, the birds of the air, the tame animals, all the wild animals, and all the creatures that crawl on the earth.</span></p>
    <p class='q1'><span class='v0_1_27'><sup id='Gen.1.27' class='v0_1_27'>27</sup>God created mankind in his image;</span></p>
    <p class='q2'><span class='v0_1_27'>in the image of God he created them;</span></p>
    <p class='q2'><span class='v0_1_27'>male and female he created them.</span></p>
    <p class='m'><span class='v0_1_28'><sup id='Gen.1.28' class='v0_1_28'>28</sup>God blessed them and God said to them: Be fertile and multiply; fill the earth and subdue it. Have dominion over the fish of the sea, the birds of the air, and all the living things that crawl on the earth. </span><span class='v0_1_29'><sup id='Gen.1.29' class='v0_1_29'>29</sup> God also said: See, I give you every seed-bearing plant on all the earth and every tree that has seed-bearing fruit on it to be your food; </span><span class='v0_1_30'><sup id='Gen.1.30' class='v0_1_30'>30</sup>and to all the wild animals, all the birds of the air, and all the living creatures that crawl on the earth, I give all the green plants for food. And so it happened. </span><span class='v0_1_31'><sup id='Gen.1.31' class='v0_1_31'>31</sup>God looked at everything he had made, and found it very good. Evening came, and morning followed- the sixth day.</span></p>'''
    
    verseWord = Word(printables, excludeChars = '<>')
    verseNumber = Word(nums)
    
    supOpen, supClose = makeHTMLTags('sup')
    
    spanOpen, spanClose = makeHTMLTags('span')
    
    verseNum = supOpen + verseNumber.setResultsName('vNum') + supClose
    
    aVerse = Combine(OneOrMore(verseWord), joinString = ' ',
        adjacent = False).setResultsName('theVerse')
    
    verse = spanOpen + Optional(verseNum) + aVerse + spanClose
    
    print '##########################################################'
    print 'This works!'
    for tokens, start, end in verse.scanString(bible):
        print '{' + str(tokens.vNum) + '} ' + tokens.theVerse
        print



---
## 2014-05-24 02:53:43 - PrabhuGurumurthy - Help using delimitedList
I have a example conf file like this

    port = 100, 200, 300, ssh, ftp, telnet

I can match it using

    ident = Word(alphas + alphanums + '-_')
    portlist = delimitedList(ident, delim = ',')

What happens it the port definition is little more complete

    port = 8000:8010, ftp, telnet, ssh, 100, 200

I can again match it using:

    portrange = Group(ident + Literal(':').suppress() + ident) + Optional(Literal(',').suppress())
    portlist = delimitedList(ident, delim = ',')
    portoptions = portrange & portlist

That works too, but the portrange has to be first in the list,

How do I go about matching both zero or more portrange and zero or more portlist in any order?

#### 2014-05-24 02:56:32 - PrabhuGurumurthy
Yeah, port and '=' are being matched with `Keyword('port') + Literal('=').suppress()`,

---
## 2014-07-02 02:55:59 - nunoplopes - infixNotation is very slow
The following script takes 20 seconds to execute in my machine with latest pyparsing.
This is a strip-down version of a larger parser. In a real program, parsing the enclosed string takes 1.5 minutes.
Is there any trick to speed up parsing of these kind of expressions?

Thanks.



    def nop(toks):
      print 'parsed: ' + str(toks)
      return toks
    
    
    identifier = Word(srange('[a-zA-Z0-9_.]'))
    reg = Literal('%') + identifier
    pre_expr_atoms = reg | Regex(r'C[0-9]*') | Regex(r'-?[0-9]+')
    
    pre_expr = infixNotation(pre_expr_atoms,
                             [(Suppress('&'), 2, opAssoc.LEFT, nop),
                              (Suppress('|'), 2, opAssoc.LEFT, nop),
                              (Suppress('+'), 2, opAssoc.LEFT, nop),
                              (Suppress('-'), 2, opAssoc.LEFT, nop),
                             ])
    
    pre_bool_expr = (pre_expr + Literal('==') + pre_expr) |\
                    (pre_expr + Literal('!=') + pre_expr)
    
    
    print pre_bool_expr.parseString('((C1 & (0-C1))-C4) == ((C1 & (0-C1))-C4) & C2')



#### 2014-07-02 05:24:45 - ptmcg
After importing pyparsing, enable packrat parsing with this code:


    ParserElement.enablePackrat()


#### 2014-07-03 01:05:47 - nunoplopes
Thanks a lot!
This gave a huge performance boost to the parser.  Moving the unary operators above the binary ones (as it makes sense priority wise) also gave another boost.

---
## 2014-07-13 22:09:19 - vrvilo - `MatchFirst` truncates named results (pyparsing)
I'm using named results in pyparsing to simplify access to the results (`result['x']` is a lot more clear to me than `result[7]`). However, after making a minor change to my parser (adding an alternative using the `|` operator in one of my productions) I started getting some weird results. Here's a simplified example:

    from pyparsing import *
    abc = Literal('a') + Literal('b') + Literal('c')
    abc_z = abc | Literal('z')
    abc('k').parseString('a b c')['k']
    # ==> (['a', 'b', 'c'], {})
    abc_z('k').parseString('a b c')['k']
    # ==> 'a'

I was expecting to get the same result (`['a', 'b', 'c']`) in both cases, but after adding the `MatchFirst` alternative using `|` I only get the first token back in the named result.

Is this expected behavior that I somehow missed? If this is a bug I'm kind of surprised it hasn't already been fixed'unless I'm basically the only person using the `setResultsName` feature.

I'm using `pyparsing-2.0.2-py2.7.egg` with Python 2.7.1.

#### 2014-07-25 07:40:38 - ptmcg
You are definitely *not* the only one using setResultsName, it is most definitely a recommended best practice.

To ensure that you always get all values in abc regardless of other surrounding constructs, enclose it in a Group:


    abc = Group(Literal('a') + 'b' + 'c')



---
## 2014-07-21 18:34:31 - tony_chu - Question on parseString Optional () terms
Here is my statement code 



    
    select_term = Suppress(Keyword('SELECT', caseless=True))
        select_statement = select_term + Optional(distinct_term) + field_list + from_clause + \
                           Optional(Group(where_clause).setResultsName('properties_list')) + \
                           Optional(order_clause) + Optional(enable_clause)
    


With the code above it work fine if the input string with correct grammar. And it also can generate Exception. if the mandatory Component ('select_term + Optional(distinct_term) + field_list + from_clause') with incorrect grammar.

My Problem is When I inputted a incorrect grammar with where clause, I am not able to get Exception and the parseString method still proceed with the mandatory Component.  Anyway I can check the whole query have a correct grammar before parseString ?

Best Regards
Tony Chu

#### 2014-07-21 20:43:45 - ptmcg
When you call parseString, add the parameter `parseAll=True` - this will require that the grammar match the entire input string.
#### 2014-07-22 02:15:12 - tony_chu
Thanks
#### 2014-07-22 02:24:12 - tony_chu
Yeah! it work perfect after I add the parameter `parseAll=True`. And thanks for developed the pyparsing as it did help me a lot of effort in my projects.
#### 2014-07-22 05:25:21 - ptmcg
Glad it has worked out for you - best of luck in your pyparsing efforts!
#### 2014-07-23 12:54:15 - tony_chu
I am almost done with it. but i come out 1 last questions (Hopefully)! 

When I config the parseaction to transform the token, I am fine will string, integer and dict in python. However, when I transform the token to return a list. It always return me a parseResult object instead of a List object. Is it a behavior of this super library? (Actually, I am fine to perform the transform after parsing, but I just want to make sure I did not miss anything with it.

Many Thanks
#### 2014-07-23 12:55:24 - tony_chu
oh, it also work fine with the transformation GAE NDB Key type too.
#### 2014-07-24 14:42:31 - ptmcg
Tony - well, this has been a stumper for me for a while, too, but I revisited it and found a way!  Check out the Examples page, and pull up parsePythonValue.py .  This will parse a string of lists, tuples, dicts, floats, ints, and strings, and convert each to the correct type - EXCEPT for lists!  The trick is that pyparsing takes every data structure returned from parsing and wraps it in a ParseResults, then calls the parse actions. EXCEPT if a ParseResults is constructed with a list, you just get a ParseResults, which you have already learned.

To work around this, you need to do two things:
1. in your parse action, wrap your desired list inside a list (which will generate a single-element ParseResults containing your list)
2. add a second parse action which extracts the single element from the ParseResults, and returns it.

Add these lines to parsePythonValue.py:


    cvtList = lambda toks: [toks.asList()]
    listStr.setParseAction( cvtList, lambda x:x[0] )


This will give you actual lists now!

I'll update the examples that ship with the source release, and the online example in this wiki.

Thanks for asking!
-- Paul

---
## 2014-07-25 02:43:13 - AndreWin - parsing class definiton on python
Hi!
I have the following string: `'class point2d(object)'`

I need to parse this sting.

My parser is:

    p = Suppress('class') + Word(alphas, alphanums+'_').setResultsName('classname') + Suppress('(') + Word(alphas, alphanums+'_').setResultsName('fromclass') + Suppress(')')

Unfortunatelly for my parser string `'class point2d (object)'` is correct too. The error is that there is whitespace after point2d word. How should I modify my parser?
Thanks, Andrei.

#### 2014-07-25 23:02:31 - AndreWin
Sorry, <strong>k</strong>w_def on 2nd line (It was copy-paste of my code)
#### 2014-07-25 23:17:59 - AndreWin
Sorry, I found badly: 
#### 2014-07-26 00:57:58 - ptmcg
That example is not really a parser of Python - it is a parser of the Python source code's grammar.txt file, which *creates* a Python parser. Very similar to the ebnf.py example.  I've never done what you are doing, which is to manually create a Python parser in pyparsing.  To parse your sample string, I'd prefer if you copied or imported the code from the parsePythonValue.py example, and then explicitly defined argval as argval = parsePythonValue.listItem. This will be more explicit than using SkipTo, which is always something of a risk - what if you had an argval to parse that was a quoted string containing an argname and '=' - I guess it is a bit contrived, but is still a concern when using SkipTo in a parser. 

You also have a bug in func_def, where you use ZeroOrMore should probably be delimitedList instead, which is a shortcut for a list of items separated by commas.  ZeroOrMore would just be a succession of arguments, with no delimiting commas.

Some other points: I've found that I like this style for defining all my suppressable punctuation:


    collon,comma,lbr,rbr,eq_sign = map(Suppress,':,()=')


And instead of:



    Or(argname+eq_sign, ')'+':')


please use the operator overloads, in this case:



    argname+eq_sign ^ lbr + collon


Why use Or here? Or will always try to parse *all* the alternatives, in case there is a chance that multiple alternatives could match (if there is more than one matching alternative, Or will return the longest one). In this case, there's no chance of matching both alternatives, so just use MatchFirst (operator '|'):



    argname+eq_sign | lbr + collon


(hopefully you'll have replaced this code using the parsePythonValue.listItem as I recommended above, but I still wanted to give these notes about Or vs. MatchFirst)

I would split out an argument spec as its own expression, and Group it so that an arg and its default value would be kept together - otherwise all the argument and default tokens would get returned as just one list of strings:



    argspec = Group(argname + Optional(eq_sign + argval))
    func_def = kw_def + funcname + lbr + delimitedList(argspec) + rbr + collon


Finally, you'll want to define a bunch of Python keywords eventually, using the Keyword class, not Literal. Using Literal as you have runs the risk of mistakenly parsing the leading 'def' of a longer string, like this statement:



    default = 1000


Literal('def') would match the leading part of 'default', Keyword('def') won't. You can define all the Python keywords much like I defined the punctuation above - fortunately, Python has relatively few keywords:



    DEF,YIELD,RETURN,FOR,IF,ELSE,WHILE = map(Keyword,
    '''def yield return for if else while'''.split())


Now this is fairly easy to maintain, and your parser expressions will look like:



    func_def = DEF + funcname + lbr + delimitedList(argspec) + rbr + collon


Just some various suggestions - good luck!
#### 2014-07-26 01:46:44 - AndreWin


    from pyparsing import *
    s = 'def myfunc(a,b,c, d={'a':1,'b':2,'c':[1,3,5]}, e=('a','b','c')):'
    kw_def = Keyword('def')
    collon, comma, lbr, rbr, eq_sign = map(Suppress, ':,()=')
    funcname = Word(alphas+'_', alphanums+'_')
    argname = Word(alphas+'_', alphanums+'_')
    argval = SkipTo(argname + eq_sign | lbr + collon)
    argspec = Group(argname + Optional(eq_sign + argval))
    func_def = kw_def + funcname + lbr + delimitedList(argspec) + rbr + collon
    func_def.parseString(s)

Result: ParseException: Expected ')' (at char 47), (line:1, col:48)
It seems for me I'm unlistening...
#### 2014-07-26 01:47:41 - AndreWin
char 47 is the whitespace before 'e=...'
#### 2014-07-26 02:01:57 - AndreWin


    from pyparsing import *
    %reset srange
    load('parsePythonValue.py')
    s = 'def myfunc(a,b,c, d={'a':1,'b':2,'c':[1,3,5]}, e=('a','b','c')):'
    kw_def = Keyword('def')
    collon, comma, lbr, rbr, eq_sign = map(Suppress, ':,()=')
    funcname = Word(alphas+'_', alphanums+'_')
    argname = Word(alphas+'_', alphanums+'_')
    argval = listItem
    argspec = Group(argname + Optional(eq_sign + argval))
    func_def = kw_def + funcname + lbr + delimitedList(argspec) + rbr + collon
    func_def.parseString(s).asList()

Result: ['def', 'myfunc', ['a'], ['b'], ['c'], ['d', {'a': 1, 'c': [1, 3, 5], 'b': 2}], ['e', ('a', 'b', 'c')]]
#### 2014-07-26 02:04:43 - AndreWin
Paul, what license of parsePythonValue.py?
#### 2014-07-26 06:49:32 - ptmcg
MIT license on all the examples, just like pyparsing
#### 2014-07-26 06:51:20 - AndreWin
Thanks a lot!)
Andrei.
#### 2014-07-26 06:52:47 - ptmcg
Do you have to use this?


    load('parsePythonValue.py')


Why not this?


    from parsePythonValue import listItem


#### 2014-07-26 06:54:58 - AndreWin
I use online version of Sage (sagemath.org)
Online version: cloud.sagemath.com.
load is sage command
#### 2014-07-26 06:59:33 - AndreWin
I downloaded parsePythonValue.py file and than uploaded it on SageMathCloud. Because this file and my file (in which I create my parser) are on the same folder, I just used load function. It's just easier for me :)
#### 2014-07-25 03:24:29 - AndreWin
I found the solution:

    p = Suppress('class') + Word(alphas, alphanums+'_').setResultsName('classname') + NotAny(White(' ')) + Suppress('(') + Word(alphas, alphanums+'_').setResultsName('fromclass') + Suppress(')')

Thanks, Andrei.
#### 2014-07-25 07:00:17 - ptmcg
Glad you were able to work this out - at first I didn't see anything wrong with your second test case. Normally, those extra whitespaces are not significant, so pyparsing just skips over them.
One other tip - I'm glad to see that you are defining results names, they are definitely helpful in processing the parsed results. I found the '.setResultsName' syntax kind of wordy and distracting, so a while ago I added an alternative shortened form:


    p = Suppress('class') + Word(alphas, alphanums+'_')('classname') + NotAny(White(' ')) + Suppress('(') + Word(alphas, alphanums+'_')('fromclass') + Suppress(')')

Purely a matter of taste/style, so use whichever form you prefer.
-- Paul
#### 2014-07-25 09:14:09 - AndreWin
It's supprised for me, but I just tryied in Python:

    def some_func (a,b,c):
        return(a, b, c)

After run It emerged that such definition is quite right! I didn't know about that. Thanks.
P.S.: Where can I see syntax for this wiki? I don't know how to insert code in my post for example.
Thanks,
Andrei.
#### 2014-07-25 09:15:00 - AndreWin
Of course there are 4 whitespaces befor 'return(a,b,c)'
#### 2014-07-25 09:28:34 - ptmcg
At the top of the Home Discussion page, I have a little example of how to embed code in your comments using [[code]] tags.  (These tags have to be on a line all by themselves.)  More wikiformatting info is at .
#### 2014-07-25 09:29:34 - ptmcg
See the note on embedding code at the top of this page: 
#### 2014-07-25 23:01:07 - AndreWin


    s = 'def myfunc(a,b,c, d={'a':1,'b':2,'c':[1,3,5]}, e=('a','b','c')):'
    w_def = Suppress('def')
    funcname = Word(alphas+'_', alphanums+'_')('funcname')
    argname = Word(alphas+'_', alphanums+'_')('argname')
    collon = Suppress(':')
    comma = Suppress(',')
    lbr = Suppress('(')
    rbr = Suppress(')')
    eq_sign = Suppress('=')
    argval = SkipTo(Or(argname+eq_sign, ')'+':'))
    func_def = kw_def + funcname + lbr + ZeroOrMore(argname + Optional(eq_sign + argval)) + rbr + collon
    func_def.parseString(s)

<strong>Result</strong>
ParseException: Expected ')' (at char 12), (line:1, col:13)
What should I modify to parse argval?
Thanks,
Andrei.

---
## 2014-08-07 05:10:45 - pank1 - Ignoring comments
Hi,

I am parsing a language where identifier names can have alphnumeric and hyphen character. And there is a form of comment which begins with with 2 hyphens. I have used something similar as below for defining identifiers and comments. I want to present a simple version here.


    identifier = Word(alphanums + '-')
    oneLineComment = Literal('--') + SkipTo(lineEnd)


I call the ignore() method on the top level parser object to ignore comments. All seems to work fine but if the identifier and comment are not separated by a non-identifier character, things fall apart, as in the parsing of:


    my-identifier-- Some comment



So it seems that ignoring of comments can't deal with this situation. One wayt o get it working is:


    identifier = Combine(OneOrMore(Word(alphanums) | Word('-', max=1)))


But that doesn't look very elegant. Is there a better, simpler approach that I am missing?

Thanks
Pankaj

#### 2014-08-07 06:53:36 - ptmcg
Can identifiers start with '-'?  If not, then you can use the 2-argument form of Word to disambiguate this:


    identifier = Word(alphanums,alphanums+'-')

If 2 arguments are given to Word, the first contains the valid starting characters, and the second contains the valid body characters, if any.

-- Paul
#### 2014-08-07 06:58:50 - ptmcg
Hmm, I see now that the problem is not so much the starting character as it is that you might have doubled hyphens that appear within the identifier.

To handle that, I think your solution is about as good as you can get.  An alternative to your Word('-', max=1) might be


    identifier = Combine(OneOrMore(Word(alphanums) | ~Literal('--') + '-'))

So that before a '-' is allowed, we first verify that it is not the first '-' of '--'.

You might try some performance tests to see which runs better.
-- Paul
#### 2014-08-07 07:54:17 - pank1
Thanks for the responses Paul. Good to know that i am not doing something un-pyparsing :-)
The parser you provided seems an interesting alternative, I have just checked the performance and it is almost similar to the one I provided.

And more of all, thanks for pyparsing. It did help me develop a medium-complex parser for a language fairly quickly. One thing which I feel would be good is better out-of-the-box support for debugging While parsing nested language constructs, if it fails to match any sub-construct, the error location that is reported is the beginning of the outer most definition but generally what is useful is the specific sub construct that caused parsing to fail. I have built this myself using the debug actions and the location passed. Its basically just working out the furthest location we went into the string for parsing and reports the line from there onwards. I haven't thought about all different type of grammars and if this approach might be useful in all situations.

Pankaj
#### 2014-08-07 10:47:57 - ptmcg
Pankaj - you can suppress that backtracking and get better error messages if you replace some of your '+' operators with '-'. For instance, say your language has a command 'print' followed by a string expression. Instead of defining it as 


    Keyword('print') + stringExpr

use 


    Keyword('print') - stringExpr

Now if there is a syntax error in the string expression, it will not backtrack any further than the 'print' keyword, so will give you an error message at least a bit closer to your error. (Take care though, not to just replace all '+'s with '-'s - there are some times where you *want* the backtracking to occur.)
#### 2014-08-08 03:43:28 - pank1
Thanks Paul, was not aware of '-' operator. Can see it's value.

---
## 2014-08-07 10:45:19 - cyrfer - making objects from ParsedResults
I'm very happy to be learning PyParsing. I started a open source project to help people maintain their OGRE resource files. That format is similar to a C++ data structure, and is documented here:


I have a pretty good start on the grammar to parse the files, but now I'm getting stuck on how to turn the parsed results into a usable object that I can manipulate before serializing to a string again. I guess I will need to improve the grammar to accommodate easy access to structure members, but I would appreciate advice on this step.

My attempt to make an object from the parsed results currently looks like this:


    def test_texture(self):
            # obtain some parsing results
            grammar = ogre_parse.subreader.ReadTextureUnit()
            parsed = grammar.parseString(test_texture_unit)
    
            # test creating the model from parsed results
            model = ogre_parse.model.TextureUnit(parsed)
    
            # example desired usage of model
            self.assertEqual(model.get('texture'), 'file.ext')


which can also be seen here: .

And the constructor that accepts the parsed result basically tries to loop through the items like this:


    for k,v in parsed[0].items():
        print('TextureUnit: update( {%s:%s} )' % (k,v))
        self.properties.update({k:v})


which can be seen in 'model.py' here


But I'm confused if looping through the parsed results is ideal, and how to make the grammar allow it. Also, there are other values stored in the parsed results that this loop is missing, like the 'name' parameter defined on line 23 of 'subreader.py'. Maybe I just need to know this value (should be: albedo) is in slot zero of the parsed results?


Any suggestions or questions are much appreciated. Thanks!
John

#### 2014-08-08 03:40:55 - pank1
Paul, as an alternative, I have found setParseActions to be a nice and  very powerful approach. Once you get a feel of them you can quickly turn the tokens into structure of your preference. You also benefit by keeping the grammar clean as no longer need most of those Group and setResultName.

 BTW, you can also increase the textarea size by dragging from the bottom right corner.
#### 2014-08-15 08:58:19 - cyrfer
@pank1: Thank you for pointing out the little handle in the corner.

@ptmcg: I have another question. I feel pretty confident in my pyparsing skills now. I'm successfully parsing most of the OGRE script format, using the tips you showed above. Unfortunately, I'm stuck on an embarrassingly simple expression. The parser 'names' are not showing up in the results, but only for this one class of parsers - the Pass Colors. I'm successfully using names and parser actions ALL OVER the place - so I'm baffled why this is a problem for me.

This test shows the grammar definitions and #the desired usage in comments.


    test_ambient_3 = 'ambient 0.1 0.2 0.3'
    test_diffuse_3 = 'diffuse 0.1 0.2 0.3'
    test_emissive_3 = 'emissive 0.1 0.2 0.3'
    test_specular_3 = 'specular 0.1 0.2 0.3 25.0'
    
    test_ambient_4 = 'ambient 0.1 0.2 0.3 1.0'
    test_diffuse_4 = 'diffuse 0.1 0.2 0.3 1.0'
    test_emissive_4 = 'emissive 0.1 0.2 0.3 1.0'
    test_specular_4 = 'specular 0.1 0.2 0.3 1.0 25.0'
    
    class TestColorParsers(unittest.TestCase):
        def setUp(self):
            realspec = Regex(r'\d+\.\d*')
            integerspec = Word(nums)
            real = (integerspec ^ realspec).setParseAction(lambda t: float(t[0]))
    
            color3spec = Group(real('r') + real('g') + real('b')).setParseAction(ogre_parse.basemodel.Color)
            color4spec = Group(real('r') + real('g') + real('b') + real('a')).setParseAction(ogre_parse.basemodel.Color)
            colorspec = ( color3spec ^ color4spec )('args')
    
            # define parsers
            self.ambient = Group(Keyword('ambient').suppress() + colorspec)('ambient')
            self.diffuse = Group(Keyword('diffuse').suppress() + colorspec)('diffuse')
            self.emissive = Group(Keyword('emissive').suppress() + colorspec)('emissive')
    
            specularspec = (color3spec('color') + real('shininess')) ^ (color4spec('color') + real('shininess'))
            self.specular = Group(Keyword('specular').suppress() + specularspec)('specular')
    
        def test_color_3(self):
            amb3 = self.ambient.parseString(test_ambient_3)
            dif3 = self.diffuse.parseString(test_diffuse_3)
            emi3 = self.emissive.parseString(test_emissive_3)
            spe3 = self.specular.parseString(test_specular_3)
    
            c = ogre_parse.basemodel.Color([[0.1, 0.2, 0.3, 1.0]])
    
            print('amb3 = %s ' % amb3)
            print('dif3 = %s ' % dif3)
            print('emi3 = %s ' % emi3)
            print('spe3 = %s ' % spe3)
    
            # desired usage in comments
            self.assertEqual(c, amb3[0][0]) # amb3.ambient
            self.assertEqual(c, dif3[0][0]) # dif3.diffuse
            self.assertEqual(c, emi3[0][0]) # emi3.emissive
            self.assertEqual(c, spe3[0][0]) # spe3.color
            self.assertEqual(25.0, spe3[0].shininess)


When running the test, the terminal shows this:


    ogre_parse.basemodel.Color: why are we comparing with _None_?
    ogre_parse.basemodel.Color: why are we comparing with __?
    ogre_parse.basemodel.Color: why are we comparing with _[]_?
    amb3 = [[Color(0.10, 0.20, 0.30, 1.00)]] 
    dif3 = [[Color(0.10, 0.20, 0.30, 1.00)]] 
    emi3 = [[Color(0.10, 0.20, 0.30, 1.00)]] 
    spe3 = [[Color(0.10, 0.20, 0.30, 1.00), 25.0]] 


The 3 logs (ogre_parse.basemodel.Color: why are we comparing with XXX) are coming from parsing the specular color, not the other colors. These logs are coming from the Color structure's __eq__ method, which I had to implement for my unit tests. I'm confused why the 'Color.__eq__' method is used during parsing, but that is not my real problem. My real problem is what did I do wrong so that I can't use the following to acccess the colors?


    self.assertEqual(c, amb3.ambient)
    self.assertEqual(c, dif3.diffuse)
    self.assertEqual(c, emi3.emissive)
    self.assertEqual(c, spe3.color)
    self.assertEqual(c, spe3.shininess)


FYI 1: It is tricky to find this 'discussion forum'. The 'Getting Help' tab says 'use discussion tab on the pyparsing home page', but there is no tab called 'discussion'.
FYI 2: I forgot where to read about formatting forum posts. It would be helpful if this page had a link called 'formatting forum posts'.
#### 2014-08-15 09:01:46 - cyrfer
You can see the code above at, line 77, 

FYI 3: I clicked 'Post', but nothing happened. I waited a while, then clicked again. Sorry for the double-post above.
#### 2014-08-15 22:10:32 - ptmcg
These comparisons happen inside pyparsing when creating a new ParseResults object - the init args are compared to None, '', and [].

The issue is in your Color class's `__eq__` method.  I wrote a small dummy version to get your code to run, and it looks like this:


    class Color(object):
        def __init__(self, tokens):
            self.tokens = tokens
        def __str__(self):
            return '%s:%s' % (self.__class__.__name__, self.tokens)
        def __eq__(self, other):
            return self.tokens == other.tokens
        __repr__ = __str__


I got this error when running your code:


    Traceback (most recent call last):
      File 'cc.py', line 66, in <module>
        t.test_color_3()
      ...
      File 'C:\Users\Paul\Desktop\pyparsing.py', line 303, in __init__
        if not toklist in (None,'',[]):
      File 'cc.py', line 20, in __eq__
        return self.tokens == other.tokens
    AttributeError: 'NoneType' object has no attribute 'tokens'


You can just see in the call stack the snippet of code where the constructor for a ParseResults is compared against None, '', and [].

To correct it, I had to make the Color class's `__eq__` method first verify the object type of the other arg:


    def __eq__(self, other):
            return isinstance(other, Color) and self.tokens == other.tokens


The real fix is for me to make this test inside pyparsing more type-aware, to guard against 
custom objects with type-unaware `__eq__` methods.  I have a change that adds this type check, and will check it into SVN this evening.

Thanks!
-- Paul
(I cleaned up the double-post - not a problem.)
#### 2014-08-18 14:18:08 - cyrfer
Hi Paul,
Thanks for looking into this, and thanks for changing pyparsing to watch out for the likes of my code.

I added a line at the top of my Color `__eq__` method,


    def __eq__(self, other):
        if not isinstance(other, Color):
            return False
        ...the other stuff...


But that did not affect my output. I still do not see the result names that I am expecting. Do you think the result names should have improved also? You may have missed my comment, buried in my last post:

My real problem is what did I do wrong so that I can't use the following to acccess the colors?
#### 2014-08-18 14:25:41 - cyrfer
Ah haa! I printed the results with `print(results.dump('- '))` and now I see the names. I guess print(results) does not show the result names. I was able to get pretty close to the usage I want:


    self.assertEqual(c, amb3.ambient[0])


#### 2014-08-19 05:25:35 - ptmcg
Yes, use dump() to see the resulting structure of the ParseResults object (the string arg is optional, so that you can print the results with a leading indent as part of a larger log string - I usually just call result.dump()).
#### 2014-09-17 09:48:04 - cyrfer
Paul, I could use your help one more time. I have a unit test that is failing and I don't see how. I've probably got another concept to learn.

The text causing the problem is:


    texture_unit
    {
        texture_alias alias
        texture file.ext
    }


If I swap the 2 inner lines (texture_alias and texture), I don't get a parsing error. I am using the 'and' (ampersand) operator to prevent ordering requirements.

The code responsible for parsing is found in the 'ogre_parse.subreader.ReadTextureUnit' class:



and I've copied it here for convenience:


    class ReadTextureUnit(ReadBase):
        def __init__(self):
            textureResourceDecl = oneOf('texture anim_texture cubic_texture')('resource_type')
    
            texPropList = Group(identspec('name') + \
                          Optional( oneOf('1d 2d 3d cubic') )('type') + \
                          Optional(integer)('numMipMaps') + \
                          Optional(Literal('alpha'))('alpha') + \
                          Optional(oneOf(imageFormats)) + \
                          Optional(Literal('gamma')))
            textureResource = Group( textureResourceDecl + texPropList('resource_properties') )('required')
    
            # the optional members
            texturePropNameList = '''
            texture_alias
            tex_coord_set tex_address_mode tex_border_colour
            filtering
            '''
            texturePropName = oneOf( texturePropNameList )
    
            # --- define the parser
            textureDecl = Keyword('texture_unit').suppress() + Optional(ident)('name') + \
                            lbrace + \
                                (textureResource & dictOf(texturePropName, propList)('properties')) + \
                            rbrace
    
            texture_ = Group(textureDecl).setParseAction(MTextureUnit)
            super(ReadTextureUnit, self).__init__(texture_('texture_unit'))


I enjoy using PyParsing tremendously. I have not yet found a great way to interpret the parsing exception messages. If I turn on debug when parsing, the output can be overwhelming for my larger parsers. Luckily this is a lower-level parser. Here is the output for the error I see:


    Testing started at 9:45 AM ...
    Match Group:({Suppress:('texture_unit') [W:(abcd...,abcd...)] Suppress:('{') {Group:({Re:('texture|anim_texture|cubic_texture') Group:({W:(abcd...,abcd...) [Re:('1d|2d|3d|cubic')] [W:(0123...)] ['alpha'] [Re:('PF_L8|PF_L16|PF_A8R8G8B8|PF_A8B8G8R8|PF_A8|PF_A4L4|PF_BYTE_LA|PF_R5G6B5|PF_B5G6R5|PF_R3G3B2|PF_A4R4G4B4|PF_A1R5G5B5|PF_R8G8B8A8|PF_R8G8B8|PF_B8G8R8A8|PF_B8G8R8|PF_X8R8G8B8|PF_X8B8G8R8|PF_A2R10G10B10|PF_A2B10G10R10|PF_DXT1|PF_DXT2|PF_DXT3|PF_DXT4|PF_DXT5|PF_FLOAT16_RGBA|PF_FLOAT16_RGB|PF_FLOAT16_R|PF_FLOAT32_RGBA|PF_FLOAT32_RGB|PF_FLOAT32_R|PF_SHORT_RGBA|PF_FLOAT16_GR|PF_FLOAT32_GR|PF_DEPTH|PF_SHORT_GR|PF_SHORT_RGB|PF_PVRTC_RGB2|PF_PVRTC_RGBA2|PF_PVRTC_RGB4|PF_PVRTC_RGBA4|PF_R8|PF_RG8')] ['gamma']})}) & Dict:([Group:({Re:('texture_alias|tex_coord_set|tex_address_mode|tex_border_colour|filtering') Group:({{~{Suppress:(LineEnd)} {Re:('\\d+\\.\\d*') | W:(0123...) | W:(abcd...,abcd...)}}}...)})]...)} Suppress:('}')}) at loc 0(1,1)
    Exception raised:Expected '}' (at char 34), (line:4, col:19)
    
    Error
    Traceback (most recent call last):
      File 'D:\Documents\STI\code\projects\SystemsTech\SDK_various\src\Tools\ogre_parse\ogre_parse\tests_reader.py', line 237, in test_texture_unit_texturealias
        res = self.reader_.parseString(test_texture_unit_texturealias)
      File 'D:\Documents\STI\code\projects\SystemsTech\SDK_various\src\Tools\ogre_parse\ogre_parse\basereader.py', line 97, in parseString
        result = self.grammar_.parseString(txt)
      File 'C:\Python34\lib\site-packages\pyparsing.py', line 1111, in parseString
        raise exc
      File 'C:\Python34\lib\site-packages\pyparsing.py', line 1101, in parseString
        loc, tokens = self._parse( instring, 0 )
      File 'C:\Python34\lib\site-packages\pyparsing.py', line 957, in _parseNoCache
        loc,tokens = self.parseImpl( instring, preloc, doActions )
      File 'C:\Python34\lib\site-packages\pyparsing.py', line 2611, in parseImpl
        return self.expr._parse( instring, loc, doActions, callPreParse=False )
      File 'C:\Python34\lib\site-packages\pyparsing.py', line 975, in _parseNoCache
        loc,tokens = self.parseImpl( instring, preloc, doActions )
      File 'C:\Python34\lib\site-packages\pyparsing.py', line 2365, in parseImpl
        loc, exprtokens = e._parse( instring, loc, doActions )
      File 'C:\Python34\lib\site-packages\pyparsing.py', line 979, in _parseNoCache
        loc,tokens = self.parseImpl( instring, preloc, doActions )
      File 'C:\Python34\lib\site-packages\pyparsing.py', line 2611, in parseImpl
        return self.expr._parse( instring, loc, doActions, callPreParse=False )
      File 'C:\Python34\lib\site-packages\pyparsing.py', line 979, in _parseNoCache
        loc,tokens = self.parseImpl( instring, preloc, doActions )
      File 'C:\Python34\lib\site-packages\pyparsing.py', line 1582, in parseImpl
        raise ParseException(instring, loc, self.errmsg, self)
    pyparsing.ParseException: Expected '}' (at char 34), (line:4, col:19)
    


Any advice is much appreciated.
#### 2014-09-17 12:44:40 - ptmcg
I wonder if you are stumbling over this:



    textureResourceDecl = oneOf('texture anim_texture cubic_texture')('resource_type')


and the overlap of 'texture' and 'texture_alias'?  Try using this instead:



    textureResourceDecl = (Keyword('texture') | Keyword('anim_texture') | Keyword('cubic_texture'))('resource_type')


This will avoid accidentally reading the leading 'texture' of 'texture_alias' as the 'texture' keyword.

-- Paul
#### 2014-09-17 16:25:51 - cyrfer
Paul!
Your solution fixed my 'texture_unit' parser!

Unfortunately, a higher-level parser still has problems with this block. My 'material' parser is now the failure point in my unit tests. I actually tried your solution at one point, which gives me confidence that I'm thinking like a real PyParser. I did not realize another problem was causing my tests to fail.

My other problem might be that I do not know how to define a grammar that lets me mix the 'textureResourceDecl' line WITHIN the lines for the optional other parsers. I defined this property parser explicitly, and got lazy with all the other properties, because this is the is the only one that is required, and it has more values that interest me.

So, this works,


    texture_unit
    {
        texture_alias alias
        filtering none
        texture file.ext // notice the texture resource comes after all the other properties
    }


But this does not,


    texture_unit
    {
        texture_alias alias
        texture file.ext  // notice this is in the middle of 2 other properties
        filtering none
    }


Please confirm, I think this line requires an ordering of one, then the other. I am looking for an easy way to mix all of them:


    textureResource & dictOf(texturePropName, propList)('properties')


For my higher-level structures, I explicitly list each property parser with the AND operator as well as the Optional parser. I think this allows those properties to be parsed even when they are mixed. I was being lazy with the 'texture_unit' structure. I believe this problem will go away if I type a parser for each optional property. It won't hurt to go in this direction, but I did enjoy the dictionary of property names.

Thanks again.
#### 2014-09-17 18:24:57 - cyrfer
Explicitly defining a parser for each of the properties, then wrapping with Optional and accumulating an expression with the AND operator, seems to have fixed my accidental ordering requirement. Thanks for the help. I'm onto other parsing challenges now.
#### 2014-09-17 19:56:10 - ptmcg
Glad this is working better for you - best of luck in your future pyparsing efforts!
#### 2014-08-07 13:19:10 - ptmcg
What you want is to start using results names to name your individual fields (so that you *don't* have to assume that 'slot 0 is the albedo' or 'slot 7 is the rotation unless the optional translation is provided in which case rotation is in slot 10' etc.  See the following code sample to see how I attach results names to the different elements.



    from pyparsing import *
    
    sample = '''\
            // first pass
            pass
            {
                ambient 0.5 0.5 0.5
                diffuse 1.0 1.0 1.0
    
                // Texture unit 0
                texture_unit 
                {
                    texture wibbly.jpg
                    scroll_anim 0.1 0.0
                    wave_xform scale sine 0.0 0.7 0.0 1.0
                }
                // Texture unit 1 (this is a multitexture pass)
                texture_unit
                {
                    texture wobbly.png
                    rotate_anim 0.25
                    colour_op add
                }
            }
            '''
    
    LBRACE,RBRACE = map(Suppress,'{}')
    realnum = Regex(r'\d+\.\d*')
    integer = Word(nums)
    filespec = Combine(Word(printables,excludeChars='.') + '.' + Word(printables)) | quotedString
    
    #define important labels
    PASS,AMBIENT,DIFFUSE,TEXTURE_UNIT,TEXTURE,SCROLL_ANIM,\
            WAVE_XFORM,SCALE,TRANS,SINE,ROTATE_ANIM,COLOUR_OP,\
            ADD, SUB, XOR = \
        map(Keyword,'''pass ambient diffuse texture_unit texture scroll_anim 
                        wave_xform scale trans sine rotate_anim colour_op
                        add sub xor
                    '''.split())
    
    ambient_defn = Group(AMBIENT + realnum('x') + realnum('y') + realnum('z'))
    diffuse_defn = Group(DIFFUSE + realnum('x') + realnum('y') + realnum('z'))
    
    texture_defn = Group(TEXTURE + filespec('fileref'))('texture')
    scroll_anim_defn = Group(SCROLL_ANIM + realnum('x') + realnum('y'))('scroll_anim')
    wave_xform_defn = Group(WAVE_XFORM + (SCALE | TRANS)('type') + restOfLine('args'))('wave_xform')
    rotate_anim_defn = Group(ROTATE_ANIM + realnum('rotation'))('rotate_anim')
    colour_op_defn = Group(COLOUR_OP + (ADD | SUB | XOR)('type'))('colour_op')
    texture_attribute = (texture_defn | scroll_anim_defn | wave_xform_defn | rotate_anim_defn | colour_op_defn)
    texture_unit_defn = Group(TEXTURE_UNIT + LBRACE +
                    OneOrMore(texture_attribute) +
                    RBRACE )
    pass_body = ambient_defn('ambient') + diffuse_defn('diffuse') + ZeroOrMore(texture_unit_defn)('texture_units')
    
    pass_defn = Group(PASS + LBRACE + pass_body + RBRACE)
    
    parser = OneOrMore(pass_defn)('passes')
    parser.ignore('//' + restOfLine)
    
    result = parser.parseString(sample)
    
    
    for ob in result.passes:
        print ob.dump()
        for tu in ob.texture_units:
            print tu.dump(indent='- ')


This will print out an indented structure like this:



    ['pass', ['ambient', '0.5', '0.5', '0.5'], ['diffuse', '1.0', '1.0', '1.0'], ['texture_unit', ['texture', 'wibbly.jpg'], ['scroll_anim', '0.1', '0.0'], ['wave_xform', 'scale', ' sine 0.0 0.7 0.0 1.0']], ['texture_unit', ['texture', 'wobbly.png'], ['rotate_anim', '0.25'], ['colour_op', 'add']]]
    - ambient: ['ambient', '0.5', '0.5', '0.5']
      - x: 0.5
      - y: 0.5
      - z: 0.5
    - diffuse: ['diffuse', '1.0', '1.0', '1.0']
      - x: 1.0
      - y: 1.0
      - z: 1.0
    - texture_units: [['texture_unit', ['texture', 'wibbly.jpg'], ['scroll_anim', '0.1', '0.0'], ['wave_xform', 'scale', ' sine 0.0 0.7 0.0 1.0']], ['texture_unit', ['texture', 'wobbly.png'], ['rotate_anim', '0.25'], ['colour_op', 'add']]]
    - ['texture_unit', ['texture', 'wibbly.jpg'], ['scroll_anim', '0.1', '0.0'], ['wave_xform', 'scale', ' sine 0.0 0.7 0.0 1.0']]
    - - scroll_anim: - ['scroll_anim', '0.1', '0.0']
    -   - x: 0.1
    -   - y: 0.0
    - - texture: - ['texture', 'wibbly.jpg']
    -   - fileref: wibbly.jpg
    - - wave_xform: - ['wave_xform', 'scale', ' sine 0.0 0.7 0.0 1.0']
    -   - args:  sine 0.0 0.7 0.0 1.0
    -   - type: scale
    - ['texture_unit', ['texture', 'wobbly.png'], ['rotate_anim', '0.25'], ['colour_op', 'add']]
    - - colour_op: - ['colour_op', 'add']
    -   - type: add
    - - rotate_anim: - ['rotate_anim', '0.25']
    -   - rotation: 0.25
    - - texture: - ['texture', 'wobbly.png']
    -   - fileref: wobbly.png
    


The names show how you can access the values in object attribute-like style by following a path:



    ob.ambient.x
    ob.diffuse.z
    ob.texture_units[0].texture


If you have actuall classes you want to build, then you can pass the parsed tokens to a constructor or classmethod - insert code like this before the definition of pass_body:



    class AmbientStruct(object):
        def __init__(self, tokens):
            self.x = float(tokens[0].x)
            self.y = float(tokens[0].y)
            self.z = float(tokens[0].z)
        def __str__(self):
            return 'Ambient(%.2f/%.2f/%.2f)' % (self.x,self.y,self.z)
        __repr__ = __str__
    ambient_defn.setParseAction(AmbientStruct)


The parse action is called at parse time, and values returned by the parse action will replace the parsed tokens in the final results. Since we pass the class name, the class constructor and initializers are called and a class instance is returned, so this is what you get in the parsed output instead of a pyparsing ParseResults object.

Now print out ob.ambient and you get:



    Ambient(0.50/0.50/0.50)


-- Paul

#### 2014-08-07 18:01:50 - cyrfer
Hi Paul,

Thanks for the eye-opening demo of pyparsing. That was exactly what I was looking for. The rest of this post is just observations, no real questions anymore.

One twist on the problem is that very few of the members are required for the 'outer' grammar types (e.g. 'pass' does not require the 'ambient' data to be present, or any other members for that matter), which probably means I just need to wrap each optional member like: Optional(ambient_defn('ambient')). More importantly, I just figured out that I can test if a member is available - because when it is not, it returns None, e.g. if not tokens[0].diffuse. This will be very helpful when I do set the parser action for one of the 'outer' grammars with few required internal members (e.g. pass) to be my actual class (e.g. PassStructure).

I'm now defining actual classes for the inner types like you showed (ambient, diffuse, etc.), and I'm assigning those classes as the parse action. When combined with the ('name') syntax, I'm seeing beautiful results. You can see my adaptation of your code below.

To be more flexible on the number of color components listed, I am trying to make an array of values until I the parser hits the LineEnd.


    EOL = LineEnd().suppress()
        realspec = Regex(r'\d+\.\d*').setParseAction(lambda t: float(t[0]))
        colorspec = Group(~EOL + OneOrMore(realspec))('vector').setParseAction(ColorStructure)


This works great for the colors, and allows the data file to only have less than 4 components (4th can be assumed to be 1.0).

Unfortunately, the specular color data should be followed by another real number that is the pass's 'shininess' value. The 
grammar seems easy if I require specular to have 4 components, but it should also OK if the color has only 3 
components. I guess I need a 'longest match' (^) for this scenario, where the 5 real numbers makes for 'R G B A shininess', and 4 real numbers makes for 'R G B shininess'. I was trying to use the EOL in my code above to be the thing that signals the end of the data because I think the format spec uses EOL too, but maybe I should go back to your way.

Thank you for the amazing tool and support.

FYI: The HTML `<textarea>` is crazy small on these forums. I am seeing ~2.5 rows when typing. 
Adding the attribute `'rows='10'` to the DOM element in Chrome made editing much nicer.

#### 2014-08-07 20:40:38 - ptmcg
Nice tip on the page layout, but I just take the wikispaces defaults on the pages. 
Personally, unless I'm just doing a short comment like this, I'll edit in a separate editor 
(SciTE is my favorite), and then copy/paste into this teeny edit window.

---
## 2014-08-12 16:11:31 - rh0dium - Small problem with recurssion - I'm sooo close..
Hi there,

I'm having a small issue with recursion.  I'm close but I'm not there yet. Given the following input:

    s = 'a1{b2{a3|b3}c2{d3|e3}e2{a4}}b1{a6|b7}'

We should be able to get the appropriate dictionary on the way out.

    data = parse_tree_to_dict(s)
    assert data == {
        'a1': {
            'b2': ['a3', 'b3'],
            'c2': ['d3', 'e3'],
            'e2': 'a4'},
        'b1': ['a6', 'b7']
    }, 'Nice try.. {} is wrong'.format(data)


Here is what I have so far..

    def parse_tree_to_dict(data):
        import pyparsing as pp
    
        lbrace = pp.Literal('{').suppress()
        rbrace = pp.Literal('}').suppress()
    
        _printables = list(pp.printables) + [' ']
        _printables.pop(_printables.index('|'))
        _printables.pop(_printables.index('}'))
        _printables.pop(_printables.index('{'))
        _printables = ''.join(_printables)
    
        word_pattern = pp.Word(_printables)
        list_pattern = pp.delimitedList(pp.OneOrMore(word_pattern), '|')
    
        enclosed = pp.Forward()
    
        atom = pp.Group(lbrace + list_pattern + rbrace)
        enclosed << ((pp.OneOrMore(word_pattern + atom)) | atom )
    
        result = enclosed.parseString(data)
    
        pprint(result.asList())
        return result


But I've got the recursion piece slightly messed up.  Can someone point me in the right direction.

Thanks

#### 2014-08-12 16:18:34 - rh0dium
Hi there,

I'm having a small issue with recursion. I'm close but I'm not there yet. Given the following input:

    s = 'a1{b2{a3|b3}c2{d3|e3}e2{a4}}b1{a6|b7}'


We should be able to get the appropriate dictionary on the way out.



    data = parse_tree_to_dict(s)
    assert data == {
    'a1': {
    'b2': ['a3', 'b3'],
    'c2': ['d3', 'e3'],
    'e2': 'a4'},
    'b1': ['a6', 'b7']
    }, 'Nice try.. {} is wrong'.format(data)


Here is what I have so far..


    def parse_tree_to_dict(data):
        import pyparsing as pp
        
        lbrace = pp.Literal('{').suppress()
        rbrace = pp.Literal('}').suppress()
        
        _printables = list(pp.printables) + [' ']
        _printables.pop(_printables.index('|'))
        _printables.pop(_printables.index('}'))
        _printables.pop(_printables.index('{'))
        _printables = ''.join(_printables)
        
        word_pattern = pp.Word(_printables)
        list_pattern = pp.delimitedList(pp.OneOrMore(word_pattern), '|')
        
        enclosed = pp.Forward()
        
        atom = pp.Group(lbrace + list_pattern + rbrace)
        enclosed << ((pp.OneOrMore(word_pattern + atom)) | atom )
        
        result = enclosed.parseString(data)
        
        pprint(result.asList())
        return result
    



---
## 2014-09-07 00:35:14 - AndreWin - Parsing units on Russian
Hello!
I'd like to parse units on Russian.
I wrote the following code:


    num_sign = Literal('+') | Literal('-')
    number = Word(nums)
    int_number = Combine(num_sign + number)
    float_number = Combine(int_number + Optional('.'+int_number) + Optional('e'+int_number))
    
    mul_sign = Suppress('*')
    div_sign = Suppress('/')
    exp_sign = Suppress('^')
    lparent = Suppress('(')
    rparent = Suppress(')')
    
    dim_word = Group(Word(alphas) + Optional(exp_sign + float_number))
    dim_group = lparent + dim_word + OneOrMore(mul_sign | div_sign + dim_word) + rparent
    
    dim_expr = dim_word | dim_group + ZeroOrMore((mul_sign | div_sign) + (dim_word | dim_group))

When I try units on Russian my code doesn't work.
Also I can't understand why N*m is parsed wrong. (My parser sees only 'N', not 'm')
Thanks,
Andrei.

#### 2014-09-07 00:46:46 - AndreWin

---
## 2014-09-18 00:41:16 - gustible - Multi-Line Parsing
I have what should be a simply case - but suspect I am misunderstanding the basics.
I want to parse a file of this format:


    start:name
    token:aaa bbb ccc
    token:ddd ee fff
    end:

Where the number of 'token: lines' are an arbitrary number of lines. The file can contain one or more of these blocks, separated by empty lines.
The following works fine (note - no 'end:' token) :


    z = 'start:name\ntoken:aa bb cc\n'
    EOL = LineEnd().suppress()
    SOL = LineStart()
    word = Word(printables)
    word_group = Group(OneOrMore(word))
    start_token = Literal('start:').suppress()
    start_marker = start_token + word
    line_token = Literal('token:').suppress()
    line = line_token + word_group.setResultsName('LINE') + EOL
    parser = OneOrMore(start_marker.setResultsName('START') + line)

Which results in :

    parseresult.START = ['name']

and

    parseresult.LINE = ['aa', 'bb', 'cc']

Now I modify the file to add an 'end:' token, and modify the code to expect an 'end:' token:


    z = 'start:name\ntoken:aa bb cc\nend:'
    EOL = LineEnd().suppress()
    SOL = LineStart()
    word = Word(printables)
    word_group = Group(OneOrMore(word))
    start_token = Literal('start:').suppress()
    start_marker = start_token + word
    line_token = Literal('token:').suppress()
    end_token = Literal('end:').suppress()
    line = line_token + word_group.setResultsName('LINE') + EOL
    parser = OneOrMore(start_marker.setResultsName('START') + line + end_token)

And now the process fails.
What am I doing wrong here ? This is a simple case, and I must be missing something very obvious.
Thank you in advance

#### 2014-09-18 04:44:52 - ptmcg
Don't you expect to have OneOrMore lines in each group?  Right now you will only parse one and then expect the end_token, which will fail in the case of having multiple token: lines in a group (but should succeed if you have only one).

#### 2014-09-18 23:01:38 - gustible
Thanks for your respnse.
Yes, I do expect one or more toke:lines in a group. But my problem is that the code above fails for a single token:line. 
The test data looks like this:


    start:name
    token:aa bb cc
    end:

as represented by the variable


    z  = 'start:name\ntoken:aa bb cc\nend:'

Parsing is using parseString fails with a message - 'Exception raised:Expected 'end:' (at char 31), (line:4, col:1)', which is at a position just past the last character in the string.
I also tested it with an additional definition of :


    lines = OneOrMore(line)
    parser = OneOrMore(start_marker.setResultsName('START') + lines + end_token)

It still fails with the same message in the exception. I am unable to identify the problem - as I said, it should be a very simple use case. 
I suspect it may have something to do with the use of LineEnd() and LineStart() - but cannot pinpoint the issue despite extensive testing.
Thanks in advance.
#### 2014-09-19 01:52:48 - ptmcg
Ah, the issue is that your definition of _word_ is `'Word(printables)'`, which will also match 'end:', and <em>word_group</em> is just OneOrMore of these - so <em>word_group</em> is just reading too many <em>word</em>'s. You can see this for yourself if you add 'word.setDebug()' after the definition of <em>word</em>, and rerun your test.  You'll see that the 'OneOrMore(word)' is reading past the EOL and including the 'end:' as part of the <em>word_group</em> (this would also consume any 'token:' markers, also not what you want). Since you want your <em>word_group</em> to end at the end of line, you can have it lookahead and stop at the EOL by modifying your definition of <em>word_group</em> to 'word_group = Group(OneOrMore(~EOL + word))'. After I make this change in your sample, things are looking better.

Now, to support multiple 'token:' lines, you will need to make a couple more changes. The first, as I mentioned before, will be to add repetion of <em>line</em> in <em>parser</em>:



    parser = OneOrMore(start_marker.setResultsName('START') + OneOrMore(line) + end_token)


I modified your test input string to 'start:name\ntoken:aa bb cc\ntoken: zzz\nend:' to test this. The modified parser will now process the input successfully. But the results name 'LINE' will only report the last group parsed. To get all of the matching word_group's in the LINE results name, change <em>line</em> to:



    line = line_token + word_group.setResultsName('LINE', listAllMatches=True) + EOL


<em>listAllMatches</em> causes all of the word_group's to be reported, not just the last one.

I think you'll also find your parsers easier to read and maintain if you change the explicit calls to <em>setResultsName</em> to use the call-syntax shortcut:



    line = line_token + word_group('LINE*') + EOL
    parser = OneOrMore(start_marker('START') + OneOrMore(line) + end_token)


I've always encouraged people to use results names, but I felt that the actual 'setResultsName' function call was ugly and distracting from the flow of the parser definition. By using the shortcut notation, the results names are clearly visible, without the clutter of the actual 'setResultsName' method name.

-- Paul
#### 2014-09-19 03:30:59 - gustible
Thank you Paul - this has cleared things up. 
I have successfully used searchString to parse a similar but more complex file - but of course parseString will give results for the overall correctness of the file, while searchString will only report on the matches found. Since I want to validate the global correctness, I need to use parseString.
Your advise has been invaluable. And thanks for the tip on using shortcut for results names!

Regards
Jacques

---
## 2014-10-14 02:53:00 - cnayak12 - Need help on how to parse the repeated blocks of text to a nested dictionary
Hi,
I Have a file with text in the format below. Need to parse the below file and convert it into a dictionary so that i can print the dictionary in yaml format using yaml.dump(). Basically, i need the below file to be stored in a dictionary object after parsing.AM currently using pyparsing. Please help mw with the same.

    ### Input file format
    #### ##############
    outer_block:
    inner_block1:
    type: val1
    properties:
      key1: val1
      key2: val2
    
    inner_block1:
    type: val1
    properties:
      key1: val1
      key2: val2
    
    output file format:
    outer_block:
        inner_block1:
           type: val1
           properties:
               key1: val1
               key2: val2
    
        inner_block1:
           type: val1
           properties:
               key1: val1
               key2: val2


---
## 2014-11-17 13:23:32 - Griffon26 - error stop does not break out of Each
I am trying to parse a set of possible options with arguments. The order in which they occur doesn't matter, but each should occur only once. I was hoping to get good error reporting by using '-' after the element that matches '-one', but because of Each the error is 'Missing one or more required elements' instead of 'Expected 'onevalue' at ...'.

Please take a look at the following example code to see what I mean.



    from pyparsing import *
    
    option_one = Keyword('-one') - Keyword('onevalue')
    option_two = Keyword('-two') - Keyword('twovalue')
    
    and1grammar = option_one + option_two
    and2grammar = option_one - option_two
    eachgrammar = option_one & option_two
    
    for grammar in [and1grammar, and2grammar, eachgrammar]:
        print '--------------------'
        print 'using grammar %s' % grammar
        try:
            grammar.parseString('-one somethingelse')
        except ParseBaseException as e:
            print e
            print e.markInputline()
    


Is there a way to work around this without having to resort to post-parsing validation through setParseAction?

Regards,
Maurice.

#### 2014-11-22 12:09:37 - Griffon26
I've seen in pyparsing's code that it has to do with Each invoking tryParse and tryParse turning ParseFatalExceptions into ParseExceptions.
The latter seems inconsistent with the documentation of ParseFatalException saying: 'user-throwable exception thrown when inconsistent parse content is found; stops all parsing immediately'.
If someone can explain what part of pyparsing needs this 'downgrading' of exceptions then I'll look into a patch for fixing this.
#### 2014-11-28 13:26:27 - Griffon26
I have submitted a patch to fix this issue and two others at 

---
## 2014-11-22 04:18:48 - Griffon26 - Trivial fix to increase usefulness of Each()'s error reporting
Currently the parseImpl of Each reports the error location using the variable 'loc', which reflects the start position of the attempted match of Each.

I think it's better to report 'tmpLoc', because it will give you the location where Each couldn't match any further.

This is particularly useful when the Each fails because of repeated items. The error message will say it was missing required items, but the position will at least be just before the repeated item.

#### 2014-11-28 13:26:11 - Griffon26
I have submitted a patch to fix this issue and two others at 

---
## 2014-11-23 02:51:18 - dlxneamtu - OneOrMore issue
Hi all,

This is my first post here, hope to get it right. I'd like to understand why I get a different output between two different codes, one containing OneOrMore and teh other a fixed repetition of word patterns(which I don't want as I will not know how many repetitions there will be). If I am using OneOrMore, it seems like different lines of text or concatenated together, instead of being separated by the EOL character. Below are the two options and the results I get: 

Without OneOrMore (I get the desired output):


    configuration1 = '''
    interface Bundle50
     ip address 10.155.0.1 255.255.224.0 secondary
     ip address 10.219.0.1 255.255.224.0 secondary
    !
    '''
    def copy_substring1(string, start, end, include):
        NL = LineEnd()
        word = Word(alphanums + '.-_@')
        configLine = word+word+word+word+word + NL
        content = OneOrMore(configLine)
        element = Literal(start) + NL + content + Literal(end) + NL
        return element.searchString(string)
    result1 = copy_substring1(configuration1,'interface Bundle50', '!', '')
    
    print result1
    output =  ' '.join(result1[0]).split('\n')
    for i in output:
        print i


I get:


    interface Bundle50 
     ip address 10.155.0.1 255.255.224.0 secondary 
     ip address 10.219.0.1 255.255.224.0 secondary 
     !

And with OneOrMore:



    configuration1 = '''
    interface Bundle50
     ip address 10.155.0.1 255.255.224.0 secondary
     ip address 10.219.0.1 255.255.224.0 secondary
    !
    '''
    def copy_substring1(string, start, end, include):
        NL = LineEnd()
        word = Word(alphanums + '.-_@')
        configLine = OneOrMore(word) + NL
        content = OneOrMore(configLine)
        element = Literal(start) + NL + content + Literal(end) + NL
        return element.searchString(string)
    result1 = copy_substring1(configuration1,'interface Bundle50', '!', '')
    
    print result1
    output =  ' '.join(result1[0]).split('\n')
    for i in output:
        print i


I get:


    interface Bundle50 
     ip address 10.155.0.1 255.255.224.0 secondary ip address 10.219.0.1 255.255.224.0 secondary 
     ! 

So in the latter case there is no separation between the two lines. I don't see why, the word patter should not catch the EOL.

Can you please help?

Thanks,
Dan

#### 2014-11-23 03:55:55 - Griffon26
If line endings are significant in your grammar, you need to call ParserElement.setDefaultWhiteSpace(' \t') to exclude the newline.
Otherwise OneOrMore will happily jump over newlines as if they were spaces.

#### 2014-11-23 04:05:11 - ptmcg
Thanks for chiming in @Griffon26 - you have the right idea, although the exact method name is ParserElement.setDefaultWhitespaceChars(' \t').  And since pyparsing usually runs expandtabs on the input string before parsing, you can usually write it as ParserElement.setDefaultWhitespaceChars(' ').

-- Paul
#### 2014-11-23 10:51:24 - dlxneamtu
Excellent! Thanks guys, that did the trick.

---
## 2014-11-26 12:52:12 - Griffon26 - LineEnd() matches at StringEnd() as well. Should it?
I have a grammar for a line-based format, so I've removed newline from the default whitespace chars. I was expecting to be able to detect the absence of a newline at end of file with LineEnd's failaction, but apparently LineEnd also matches StringEnd.

I would consider this a bug. Do you agree?

I have a fix for it that involves a change in commaSeparatedList as well, but I can imagine that people are relying on this behaviour in their grammars.

Would you accept a patch that changes this behaviour?

#### 2014-11-26 16:57:10 - ptmcg
It was my intention that LineEnd would match at the end of the input string.  If you want to detect the condition of a StringEnd() that does not end with a LineEnd, you can define an expression `EOL = ~StringEnd() + LineEnd()`.

---
## 2014-12-06 09:14:40 - Griffon26 - Parsing within quotes?
I'm trying to create a grammar that can parse an expression within quotes, but that will avoid the embedded expression matching the end quote even if the expression grammar itself would allow it.

For instance, I would like this grammar:


    Quoted(Word(printables)) + StringEnd()

to reject the following text:


    'something'somethingelse'


I've attempted doing this with QuotedString and a parseAction that would further parse the tokens, but that fails when used within Each because it uses tryParse which disables parse actions.

What would be the best way to do this?

#### 2014-12-07 07:20:36 - ptmcg
Can you clarify what you intend 'Quoted(Word(printables))' to do?  Pyparsing does not have any class 'Quoted', is this something you have written? And 'Word(printables)' will consume all non-whitespace characters into the Word before trying to parse any other elements.

Your sample will fail (which is what you want) when matching either 'quotedString + StringEnd()' or 'QuotedString(''') + StringEnd()' - can you build up your question from one of these?

-- Paul
#### 2014-12-07 13:12:17 - Griffon26
Quoted was a made-up solution to show how I would imagine using it.

I'd like to be able to use something like a QuotedString, but something which would allow me to specify a grammar for the stuff within quotes.

I could use Literal(''') + mygrammarwithinquotes + Literal('''), but then when parsing my example text above the Literals may match the outer quotes and the inner quote could be (unintentionally) matched by mygrammarwithinquotes.
#### 2014-12-07 15:45:46 - ptmcg
Why can't you prevent your mygrammarwithinquotes from matching the interior quote?
#### 2014-12-08 09:28:06 - Griffon26
In principal I could, but I'd like to separate those concerns at the level where I match the quotes by basically saying 'match the string upto the next quote using this grammar'.
Otherwise I would have to make sure for every element used in mygrammarwithinquotes that it should not ever match anything that includes a quote. This would not be practical if mygrammarwithinquotes was a large hierarchy.
#### 2014-12-08 22:36:32 - ptmcg
Your question is still confusing to me, since you are talking about both 
matching a difficult string and then wanting to add some logic which will 
disable matching it.  I can only assume that the interior quote should 
be considered part of the overall quoted string because it does not have 
whitespace before or after it. Here is something that will match that:


    
    from pyparsing import *
    
    test1 = ''something'somethingelse''
    test2 = ''something' somethingelse''
    test3 = ''something 'somethingelse''
    
    QUOTE = Literal(''')
    INTERNAL_QUOTE = QUOTE.copy().leaveWhitespace()
    
    quotedStringWithEmbeddedQuotes = (
        QUOTE +
        originalTextFor(
            ZeroOrMore(Word(printables,excludeChars=''') | 
                (INTERNAL_QUOTE + ~WordEnd())
            )
        ) +
        QUOTE
    )
    
    for test in (test1,test2,test3):
        print test
        print quotedStringWithEmbeddedQuotes.parseString(test)
        print
    


prints:



    'something'somethingelse'
    [''', 'something'somethingelse', ''']
    
    'something' somethingelse'
    [''', 'something', ''']
    
    'something 'somethingelse'
    [''', 'something', ''']
    


#### 2014-12-08 22:48:39 - ptmcg
As for the principle of allowing anything within your quoted string, even double quotes, I think you are treading in ambiguous grammar territory. Having to escape delimiters is no different here than it is in regular expressions requiring '\' characters, or SQL statements requiring '' doubling of quotation marks.

Here is an interesting tangent - why are '/'s escaped in regular expressions?  It is clear why '.', '*', '?', '[', ']', '(', ')' are all escaped - they have meaning as metacharacters for the regex.  But '/' has no special meaning for regex's, why does it have to be escaped with a leading '\'?  The answer is not in re's themselves, but in their usage in applications such as vi or grep. In vi, one gives a substitution command using 's/<matching regex>/<replacement regex>/<optional qualifiers>'  If the '/'s within the regexes weren't escaped, then how would one tell the regex '/'s from the delimiting '/'s of the substitution command?  Regular expressions themselves are not confused by unescaped '/'s, but their application within the larger context makes escaping '/'s necessary, and so this gets built into the regex parser.  I think a similar rationale may need to be applied in the case of your embedded quotation marks.

---
## 2014-12-15 08:00:31 - vsvismeista - adding key\/value pair to originally ParseResults Object
Hi all,

I have made my first steps in pyparsing - it's really cool.

But I have a problem without knowing howto solve at the moment:
After parsing I want to calculate the time-difference of two results and add this result to the original ParseResult.

Here the working example of the ParseAction - where 'text' is the original Result:


    def job_structuring(text):
        start_time = text['job_start_time']
        end_time = text['job_finish_time']
        time_diff = end_time-start_time
        text.append(time_diff)
        return text

This code works perfectly.

But how can I give the 'time_diff' a name in the returned Result?

I tried to instantiate a new ParseResults Object in the ParseAction:



    def job_structuring(text):
        start_time = text['job_start_time']
        end_time = text['job_finish_time']
        time_diff = end_time-start_time
        d = ParseResults(time_diff, name='job_duration')
        text = text + d
        return text


but there comes an error if I have this line (even without the line in which I add the 'd' to the 'text') in the ParseAction:


    File 'parse.py', line 9, in process_text_search
        for tokens, start, end in getLogLineBNF().scanString(text):
      File 'C:\Python33\lib\site-packages\pyparsing.py', line 1155, in scanString
        nextLoc,tokens = parseFn( instring, preloc, callPreParse=False )
      File 'C:\Python33\lib\site-packages\pyparsing.py', line 1015, in _parseNoCache
        tokens = fn( instring, tokensStart, retTokens )
      File 'C:\Python33\lib\site-packages\pyparsing.py', line 779, in wrapper
        ret = func(*args[limit[0]:])
    TypeError: job_structuring() missing 1 required positional argument: 'text'


Could you please give me some hint?

#### 2014-12-15 11:52:01 - ptmcg
Use the dict-like access that ParseResults provide:


    text['time_diff'] = time_diff


#### 2014-12-16 02:10:14 - vsvismeista
thanks,
when I use dump it works:


    [datetime.datetime(1900, 1, 1, 0, 22, 58), datetime.datetime(1900, 1, 1, 0, 25)]
    - Id: 180961421_1
    - Nach: L4500/11D.A
    - Typ: LOADL4500/11D
    - Von: L4500/11DEQB.C
    - job_duration: 0:02:02
    - job_finish_time: 1900-01-01 00:25:00
    - job_start_time: 1900-01-01 00:22:58
    [datetime.datetime(1900, 1, 1, 0, 25, 2), datetime.datetime(1900, 1, 1, 0, 25, 28)]
    - job_duration: 0:00:26
    - job_finish_time: 1900-01-01 00:25:28
    - job_start_time: 1900-01-01 00:25:02


but when I use asXML():


    <job_start_time>
      <job_start_time>1900-01-01 00:22:58</job_start_time>
      <job_finish_time>1900-01-01 00:25:00</job_finish_time>
    </job_start_time>
    
    <job_start_time>
      <job_start_time>1900-01-01 00:25:02</job_start_time>
      <job_finish_time>1900-01-01 00:25:28</job_finish_time>
    </job_start_time>


I haven't understand yet why the job_duration isn't showed..
#### 2014-12-18 04:16:35 - ptmcg
Adding a results name does not automatically append to the ParseResults internal list, and asXML works by walking the list and looking for matching names to make the tags; dump just works off the internal dict, and so that is why you see your result.  You will need to update both the internal dict and the internal list, try:



    text['job_duration'] = time_diff
    text.append(time_diff)


Is asXML() absolutely necessary for your project, or are you just using it for debugging? I 
am not a big fan of asXML(), as it has to do a fair bit of guesswork to marry up the results 
names and the values, and sometimes asXML() will guess wrongly.  I've put more effort into 
getting dump() to work properly, especially the most recent enhancement to list out nested 
results as numbered array elements.

Glad you are finding pyparsing to be cool - good luck with your project!

-- Paul

---
## 2014-12-18 02:11:05 - perw07 - How best to traverse lists in pyparsing results?
My first post, beginner at pyparsing, haven't figured out how to traverse lists in the parsed results.

Here is my grammar:



    top = '(' item+ ')'
    item = ':' label? '(' value? item* ')'
    value = <string>
    label = <string>


So lots of recursion and 'missing' stuff.

This is my implementation:



    import pyparsing as pyp
    
    LP, RP, CN = map(pyp.Suppress, '():')
    Label = pyp.Word(pyp.alphanums)
    Value = pyp.Word(pyp.alphanums)
    Item = pyp.Forward()
    Item << pyp.Group(CN + pyp.Optional(Label)('label') +
                      LP + pyp.Optional(Value)('value') +
                      pyp.Group(pyp.ZeroOrMore(Item))('items') + RP)
    Top = LP + pyp.Group(pyp.OneOrMore(Item))('top') + RP + pyp.stringEnd


Here is sample input and my tries to extract information:


    test = '''\
    (
      :rules (ckpd
        :pre (val0)
        :mid (val1
          : extra (0)
          : empty ()
        )
        :post (val2)
        : (unlabeled1)
        : (unlabeled2)
      )
      : (anon)
    )
    '''
    
    try:
        db = Top.parseString(test)
    except pyp.ParseException as err:
        print err.markInputline()
        print err
        exit()
    
    for i1 in db.top:
        print 'i1', type(i1)
        print i1.dump()
        print 'i1.label: '' + i1.label + '''
        print 'i1.value: '' + i1.value + '''
        print 'i1.items type: ', type(i1.items)


When I run this, I get the expected output (below). My problem is that I don't know how to traverse the array labeled 'items'?


    i1 <class 'pyparsing.ParseResults'>
    ['rules', 'ckpd', [['pre', 'val0', []], ['mid', 'val1', [['extra', '0', []]]], ['post', 'val2', []], ['unlabeled1', []], ['unlabeled2', []]]]
    - items: 
      [0]:
        ['pre', 'val0', []]
        - items: []
        - label: pre
        - value: val0
      [1]:
        ['mid', 'val1', [['extra', '0', []]]]
        - items: 
          [0]:
            ['extra', '0', []]
            - items: []
            - label: extra
            - value: 0
        - label: mid
        - value: val1
      [2]:
        ['post', 'val2', []]
        - items: []
        - label: post
        - value: val2
      [3]:
        ['unlabeled1', []]
        - items: []
        - value: unlabeled1
      [4]:
        ['unlabeled2', []]
        - items: []
        - value: unlabeled2
    - label: rules
    - value: ckpd
    i1.label: 'rules'
    i1.value: 'ckpd'
    i1.items type:  <type 'instancemethod'>
    i1 <class 'pyparsing.ParseResults'>
    ['anon', []]
    - items: []
    - value: anon
    i1.label: ''
    i1.value: 'anon'
    i1.items type:  <type 'instancemethod'>



#### 2014-12-18 03:59:13 - ptmcg
Your results name 'Items' conflicts with the defined method name 'items' defined for iterating over ParseResults key-value pairs. But there is hope: try accessing your 'items' value using dict-like notation instead: 



    print i1['items']


And well done for your first pyparsing project - welcome!

-- Paul



