# Documentation

**Course:** COMPSCI 4TB3\
**Term:** 2022 Winter\
**Topic:** Translating Logic to Natural Language (Topic 11)\
**Group Number:** 19\
**Group Members:** \
1). Haoyang Tao, taoh4\
2). Huaijin Ning, ningh4\
3). Run Zhang, zhangr75


# Description of The Project

The purpose of this project is to find a method to convert logical formulas into natural language. It is known that the foundation of all mathematical reasoning is logic. Elements like symbolic sets, relations, functions, and mathematical logic are usually involved in logic formulas, which are not easy to comprehend by natural language. The common use of logic formulas is in textual specification languages and graphical specification languages to express preconditions, postconditions, invariants, and other properties. However, these expressions can be hard to read. Therefore, what we are going to do is developing a translator that translates logic structure/expressions into natural language (English sentences). Details of the project are explained below.

# Project Notebook Details

This project consists of five notebooks, named scanner, proposition_parser, predicate_parser, procedure, testcase respectively. 
- scanner: scanner of the project.
- proposition_parser: parser for propositional logic, individual classes for identifier, not, and, or, imply, equivalence.
- predicate_parser: parser for predicate logic, individual classes for exist, for all.
- procedure: procedures of concrete grammar.
- testcase: helper functions and test cases.

For more information, please check the sections below.

# Run Instructions

* Create a new cell in file `testcase.ipynb`.
* Run all the cells, especially the importing part.
* use `evaluate('<some logic formula>')` to translate the formulae.

#### Alternitive:
* Create a new cell in a new file
* Copy the following instructions in the first cell and run:
    
   ```
   %run scanner.ipynb
   %run procedure.ipynb
   %run predicate_parser.ipynb
   %run proposition_parser.ipynb
   ```
* Copy the following instructions in the second cell and run:

    ```python
    def ast(s):
        global src, pos;
        src, pos = s, 0; getChar(); getSym();
        return expression()

    def asterr(s):
        try: ast(s); return ''
        except Exception as e:
            print(e); return str(e)
    
    def evaluate(s):
        global ordinalCounter
        try:
            print(s + " \n")
            if type(ast(s)) in (int, bool): return ast(s)
            ordinalCounter = -1
            return ast(s).eval()
        except Exception as e:
            print(e); return str(e)
    ```
* use `evaluate('<some logic formula>')` to translate the formulae.

# Supported Symbols And Grammar

    symbol ::= (identifier | 'true' | 'false' | '¬' | '∧' | '∨' |
            '→' | '≡' | '∀' | '∃' | '❙' | '•' | '(' | ')' | '=' | 
            '≠' | ',' | '-' | '<' | '>' )
    identifier ::= letter {letter}
    letter ::= 'a' | ... | 'z' | 'A' | ... | 'Z'
    
Identifiers can only be a single letter, either uppercase or lowercase.


### Parser (Propositional logic only)
   

The abstract syntax tree consists of _nodes_ of following types:

- **`bool`** for boolean constants
- **`Ident(name)`** with `name` of type `str`, the identifier name
- **`Not(op, arg)`** where `op` is `NOT` and `arg` is a node for arguments
- **`And(op, left, right)`** where `op` is `AND` and `left`, `right` are nodes for the left and right argument.
- **`Or(op, left, right)`** where `op` is `OR` and `left`, `right` are nodes for the left and right argument.
- **`Imply(op, left, right)`** where `op` is `IMPLIES` and `left`, `right` are nodes for the left and right argument.
- **`Equiv(op, left, right)`** where `op` is `EQUIVALENT` and `left`, `right` are nodes for the left and right argument.


    Proposition = 
            | Identifier
            | Boolean
            | Not Proposition
            | Proposition And Proposition
            | Proposition Or Proposition
            | Proposition Implies Proposition
            | Proposition Equivalent Proposition


In the abstract syntax tree, a constant is treated as a null-ary (parameterless) function, e.g. `p ∧ (q ∨ r)`, declares a null-ary function `p`, and "calls" it.

### Parser (Predicate logic only)

The abstract syntax tree consists of _nodes_ of following types:

- **`bool`** for boolean constants
- **`Ident(name)`** with `name` of type `str`, the identifier name
- **`Forall(op, q, r, t)`** where `op` is `FORALL` and `q`, `r`, `t` are nodes for the parameter and statement arguments.
- **`Exist(op, q, r, t)`** where `op` is `EXIST` and `q`, `r`, `t` are nodes for the parameter and statement arguments.


    Predicate = 
            | Identifier
            | Boolean
            | Forall (Proposition | Predicate)
            | Exist (Proposition | Predicate)


In the abstract syntax tree, a constant is treated as a null-ary (parameterless) function, e.g. `∀ x | Q · R`, declares a null-ary function `x`, and "call" it.

### Parser (Procedures only)

Concrete grammar: 

    expression ::= relation ["≡" relation]
    relation ::= term [ "→" term]
    term ::= factor [ ("∧" | "∨" ) factor]
    factor ::= identifier 
        | "true" 
        | "false" 
        | "¬" expression
        | "∀" expression
        | "∃" expression
        | "(" expression ")" 
        
# Usage And Examples

### Usage
* `evaluate('<some logic formula>')` where `<some logic formula>` is:
    * `<Identifier> | <Bool> | <Logic Formula>` `<Binary Operation>` `<Identifier> | <Bool> | <Logic Formula>`
    * `<Unary Operation>` `<Logic Formula>`
    * `<Forall> | <Exist>` `❙` `<Logic Formula> (as range)` `•` `<Logic Formula> (as body)`
* Note: we DO NOT accept propositional logic which has no range. Instead, put `true` in the range part.

### Examples
`evaluate('true ∧ false')`\
`evaluate('¬ p')`\
`evaluate('p ∧ q')`\
`evaluate('p ∨ q')`\
`evaluate('true ∨ false')`\
`evaluate('q => p')`\
`evaluate('q -> p')`\
`evaluate('q → p')`\
`evaluate('((p ∧ r) ∧ true) ∧ (false ∧ q) ≡ (true ∧ p) ∧ (false ∧ true)')`\
`evaluate('(p ∧ (k ∨ true)) ∧ (false ∧ q) ≡ (true ∧ p) ∧ (false ∧ true)')`\
`evaluate('(∀ x | R · T)')`\
`evaluate('p ∨ (q ⇒ p) ≡ q ⇒ p')`\
`evaluate('p ∧ (q -> r) ≡ p ⇒ q -> r')`

# Reference
- Textbook by David Gries and Fred B. Schneider: A Logical Approach to Discrete Math
- Propositional Logic in Discrete Math: https://ggc-discrete-math.github.io/logic.html
- Propositional Logic Syntax: https://www.logicthrupython.org/chapter01.pdf
- Getting Started with the CalcCheck Language: http://calccheck.mcmaster.ca/CalcCheckDoc/GettingStartedWithCalcCheck.html
- Getting Started with CalcCheckWeb: http://calccheck.mcmaster.ca/CalcCheckDoc/GettingStartedWithCalcCheckWeb.html
- CalcCheck Syntax: http://calccheck.mcmaster.ca/CalcCheckDoc/2019-12-20_CalcCheck-Syntax-Hints.pdf
- CalcCheck Theorem List: https://www.cas.mcmaster.ca/~kahl/CS2DM3/2018/2DM3-2018-Mid-November-ThmReference.html
