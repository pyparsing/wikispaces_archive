## Pyparsing Wikispaces Discussion - 2018

[2018-01-03 01:54:48 - domogled - parseAction  - action is not called](./#2018-01-03-015448---domogled---parseaction----action-is-not-called)  
[2018-01-25 06:24:23 - mwiebusch78 - associativity in operatorPrecedence](./#2018-01-25-062423---mwiebusch78---associativity-in-operatorprecedence)  
[2018-02-02 03:08:36 - mrrmr - Matching empty lines verbatim](./#2018-02-02-030836---mrrmr---matching-empty-lines-verbatim)  

---
## 2018-01-03 01:54:48 - domogled - parseAction  - action is not called


    from pruga.elm import ast
    
    from pyparsing import (alphanums,
                            alphas,
                            ParserElement,
                            Keyword,
                            Suppress,
                            Word,
                            delimitedList)
    
    ParserElement.enablePackrat()
    
    class Node:
    
        def __init__(self, s, loc, tokens):
            print('init NODE WITH  TOKENS', tokens, f''{s}'')
    
    
    IMPORT = Suppress(Keyword('import'))
    
    ModuleName = Word(alphas.upper(), alphanums + '_')('name')
    
    QualifiedModuleName = delimitedList(ModuleName, delim='.')
    
    # QualifiedModuleName has not defined any parseActons
    ImportStatement = IMPORT + QualifiedModuleName('module') 
    
    # I define parseAction now, but this action will not be used
    QualifiedModuleName.setParseAction(Node)
    
    source = 'import X.Y.Z'
    ast = ImportStatement.parseString(source)
    print('ImportStatement defined before QualifiedModuleName.setParseAction(Node)')
    print(ast)
    
    # identically definition ImportStatement, but is defined after QualifiedModuleName.setParseAction(Node)
    ImportStatement = IMPORT + QualifiedModuleName('module') 
    
    ast = ImportStatement.parseString(source)
    print('The same ImportStatement defined after QualifiedModuleName.setParseAction(Node)')
    
    print(ast)
    


output

ImportStatement defined before QualifiedModuleName.setParseAction(Node)
['X', 'Y', 'Z']
init NODE WITH  TOKENS ['X', 'Y', 'Z'] 'import X.Y.Z'
The same ImportStatement defined after QualifiedModuleName.setParseAction(Node)
[\<<u>main</u>.Node object at 0x7f136483c080\>]


---
## 2018-01-25 06:24:23 - mwiebusch78 - associativity in operatorPrecedence
I am trying to understand how associativity of infix operators is handled in operatorPrecedence. The following code



    from pyparsing import *
    
    variable = Word(alphas+'_', alphanums+'_')
    parser1 = operatorPrecedence(variable, [('+', 2, opAssoc.RIGHT)])
    parser2 = operatorPrecedence(variable, [('+', 2, opAssoc.LEFT)])
    
    parsed1 = parser1.parseString('x + y + z', parseAll=True)
    print(parsed1)
    parsed2 = parser2.parseString('x + y + z', parseAll=True)
    print(parsed2)


prints



    [['x', '+', ['y', '+', 'z']]]
    [['x', '+', 'y', '+', 'z']]


I would have expected this:



    [['x', '+', ['y', '+', 'z']]]
    [[['x', '+', 'y'], '+', 'z']]


I.e. parser2 seems to flatten the expression rather than making it left-associative. Is this a bug or a feature?


---
## 2018-02-02 03:08:36 - mrrmr - Matching empty lines verbatim
Hi,
I'm writing a lexer/parser for Visual TrueType Talk, a simple command language. Input looks like:


    /* VTTTalk glyph 2, char 0x41 (A) */
    /* GUI generated July 2015 */
    
    /* Y direction */
    ResYAnchor(2,8)
    ResYAnchor(4,2)
    YIPAnchor(2,1,4)
    YInterpolate(1,16,9,13,4)
    YDelta(16,1/4@16,1/2@18)
    YDelta(9,1/4@16,5/8@18)
    YDelta(13,3/8@16,1@18)
    YShift(1,0)
    ResYLink(1,17,72)
    YShift(17,8)
    ResYAnchor(7,8)
    
    /* X direction */
    XInterpolate(18,3,2,4,16,9,5,7,8,6,19)
    Align(2,1,17,16)
    Align(7,0,8,9)
    
    Smooth()


My grammar so far:


    comment = cStyleComment
    
    point = pyparsing_common.integer
    ppem = pyparsing_common.integer
    range_of_ppems = ppem + Suppress('..') + ppem
    # range_of_ppems.setParseAction(lambda token: range(token[0], token[1] + 1))
    
    fraction = pyparsing_common.signed_integer + Suppress(
        '/') + pyparsing_common.integer
    fraction.setParseAction(lambda token: fractions.Fraction(token[0], token[1]))
    distance = pyparsing_common.signed_integer ^ fraction
    distance_ppems = delimitedList(ppem ^ range_of_ppems, delim=';')
    distance_at_ppems = distance + Suppress('@') + Group(distance_ppems)
    # distance_at_ppems.setParseAction(
    #     lambda token: Distance(token[0], token[1].asList()))
    
    angleFlag = oneOf('/ �')('angleFlag')
    controlFlag = oneOf('\<\< \>\> \<\> \>\< ||')('controlFlag')
    minimumDistanceFlag = oneOf('\< \> \<= \>=') ^ (
        Literal('\>=') + Group(distance
                              | Suppress('(') + distance + Suppress(',') + ppem +
                              Suppress(',') + distance + Suppress(')')))
    # minimumDistanceFlag.setParseAction(
    #     lambda token: MinimumDistanceFlag(token[0], token[1].asList() if token.get(1) else None)
    # )
    
    command_name = Word(alphas + '_')
    command_argument = point ^ distance ^ distance_at_ppems ^ minimumDistanceFlag
    command = command_name + Optional(angleFlag ^ controlFlag) + nestedExpr(
        content=delimitedList(command_argument))
    # command.setParseAction(construct_command)
    
    p = OneOrMore(comment | command)


I want to preserve empty lines as they are for roundtrip testing. Matching 'EOL = ~StringEnd() + LineEnd()' matches each '\n', but not empty lines as such. I want the final token list to look like '['/* VTTTalk glyph 2, char 0x41 (A) */', '/* GUI generated July 2015 */', '', '/* Y direction */', \<my object\>, ...]'. How?




