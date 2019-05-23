# Compiler Lectures

- [Lecture 1](#lecture-1)
- [Lecture 2](#lecture-2)
- [Lecture 3](#lecture-3)
- [Lecture 4](#lecture-4)
- [Lecture 5](#lecture-5)
- [Lecture 6](#lecture-6)
- [Other resources](#other-resources)

## Lecture 1

Compiler
: a program that takes a program written in a source language and translates it into an equivalent program in a target language.<br><br>

**Techniques** used in compiler design are applicable to many computer science problems. <br><br>

| Techniques used in | Can be used in                                                                 |
|:-------------------|:-------------------------------------------------------------------------------|
| lexical analyzer   | text editors,information retrieval system, and pattern recognition programs    |
| parser             | query processing system such as SQL                                            |
| compiler design    | - Natural Language Processing (NLP) <br> - Software having a complex front-end |

### Parts of a Compiler

|                   | Analysis                                                                 | Synthesis                                                                       |
|:------------------|:-------------------------------------------------------------------------|:--------------------------------------------------------------------------------|
| **In this phase** | An intermediate representation is created from the given source program. | The equivalent target program is created from this intermediate representation. |
| **Parts**         | - Lexical Analyzer <br>- Syntax Analyzer <br>- Semantic Analyzer         | - Intermediate Code Generator<br>- Code Generator<br>- Code Optimizer           |

### Phases of a Compiler

From source program to target program, the compiler goes through the following phases.

| Phase                                                       | what happens                                                                                                                                        |
|:------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------|
| [Lexical Analyzer](#lexical-analyzer)                       | reads the source program character by character and returns the [tokens](#token) of the source program.                                             |
| [Syntax Analyzer](#syntax-analyzer) (parser)                | creates the syntactic structure (generally a parse tree) of the given program.                                                                      |
| [Semantic Analyzer](#semantic-analyzer)                     | checks the source program for semantic errors and collects the type information for the code generation.                                            |
| [Intermediate Code Generator](#intermediate-code-generator) | produces an explicit intermediate codes representing the source program. These intermediate codes are generally machine (architecture) independent. |
| [Code Optimizer](#code-optimizer)                           | optimizes the code produced by the intermediate code generator in the terms of time and space.                                                      |
| [Code Generator](#code-generator)                           | Produces the target language in a specific architecture. The target program is normally is a relocatable object file containing the machine codes.  |

Each phase transforms the source program from one representation into another. <br>
They communicate with:

- error handlers.
- the symbol table.

### Lexical Analyzer

> - Puts information about identifiers into the symbol table.
- Regular expressions are used to describe tokens (lexical constructs).
- A (Deterministic) Finite State Automaton can be used in the implementation of a lexical analyzer.

<p id="token"></p> <!-- for reference to token on phases of a compiler  -->

A Token
: describes a pattern of characters having same meaning in the source program. (such as identifiers, operators, keywords, numbers, delimiters and so on)

Example: <br>
newval := oldval + 12

| Lexemes | Tokens              |
|:--------|:--------------------|
| newval  | identifier          |
| :=      | assignment operator |
| oldval  | identifier          |
| +       | add operator        |
| 12      | a number            |

### Syntax Analyzer

> Checks whether a given program satisfies the rules implied by a CFG or not. If it satisfies, the syntax analyzer creates a parse tree for the given program.

#### Parse Tree

![parse tree](http://img.c4learn.com/2012/01/Parse-Tree-Syntax-Analysis-in-Compiler-Design.jpg) <br>
In a parse tree,
* All terminals are at leaves.
* All inner nodes are non-terminals in a CFG.

_syntax of a language_ is specified by a __CFG__ (CFG rules are mostly recursive) <br>
we use BNF to specify a CFG <br><br>
Example:

~~~~
assgstmt   -> identifier := expression
expression -> identifier
expression -> number
expression -> expression + expression
~~~~

*[CFG]: Context Free Grammar
*[BNF]: Backus Naur Form
*[]()* <!-- just to fix the bold thought by the text editor -->

#### Syntax Analyzer :vs: Lexical Analyzer

##### Which constructs recognized by lexical analyzer, and which by syntax analyzer?

- Both of them do similar things; ~~But~~

|            | Lexical Analyzer                                                                                                         | Syntax Analyzer                                                                                                                    |
|:-----------|:-------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------|
| deals with | simple non-recursive constructs of the language                                                                          | recursive constructs of the language                                                                                               |
|            | - simplifies the job of the syntax analyzer <br> - recognizes the smallest meaningful units (tokens) in a source program | works on the smallest meaningful units (tokens) in a source program to recognize meaningful structures in our programming language |

#### Parsing Techniques

|                                       | Top-Down :arrow_down:                                                        | Bottom-Up :arrow_up: (shift-reduce parsing)                                                                                                |
|:--------------------------------------|:-----------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| Construction of the parse tree starts | from root towards leaves                                                     | from leaves towards root                                                                                                                   |
| Efficient parsers                     | easily constructed by hand                                                   | created with the help of some software tools                                                                                               |
|                                       | Recursive Predictive Parsing, Non-Recursive Predictive Parsing (LL Parsing). | Operator-Precedence Parsing – simple, restrictive, easy to implement LR Parsing – much general form of shift-reduce parsing, LR, SLR, LALR |

### Semantic Analyzer

> - Type-checking is an important part
- semantic information cannot be represented by a context-free language
- CFGs used in the syntax analysis are integrated with attributes (semantic rules)

The result is a syntax-directed translation (Attribute grammars)<br>

Example:

~~~~
newval := oldval + 12    # The type of the identifier newval must match with type of the expression (oldval+12)
~~~~

### Intermediate Code Generation
> The level of intermediate codes is close to the level of machine codes.

Example:

~~~~
newval := oldval * fact + 1
~~~~

:arrow_down:

~~~~
id1 := id2 * id3 + 1
~~~~

Intermediates Codes :arrow_down: (Quadraples)

~~~~assembly
MULT id2,id3,temp1
ADD temp1,#1,temp2
MOV temp2,,id1
~~~~


### Code Optimizer

~~~~assembly
MULT id2,id3,temp1
ADD temp1,#1,id1
~~~~

### Code Generator

Example: <br>
(assume that we have an architecture with instructions
whose at least one of its operands is a machine register)

~~~~assembly
MOVE id2,R1
MULT id3,R1
ADD #1,R1
MOVE R1,id1
~~~~



## Lecture 2

### Lexical Analyzer:
  It reads the source program character by character to produce tokens.<br>

* Normally a lexical analyzer doesn’t return a list of tokens at one shot, it returns a token when the parser asks a token from it.<br><br>

### Tokens:

- Represents a set of strings described by a pattern.
- Additional information should be held for that specific lexeme. This additional information is called as the attribute of the token.
- Token type and its attribute uniquely identifies a lexeme.
- Regular expression is used to specify tokens.

<br><br>

### Concepts of Languages:

- Alphabet: set of finite symbols.
- String: sequence of symbols on an alphabet.
- Language: consists of set of strings.
- Operation on Language:
    - Concatenation
    - Union
    - Exponentiation
    - Kleen Closure "\*"
    - Positive Closure "+"
<br>

### Regular Expressions:

  - Used to describe tokens.
  - Normally, they are built up of simpler regular expressions.
  - Regular set: a language denoted by a regular expression.

### Presedence Rules in Regular Expressions:

  1. Parentheses
  2. \* "Kleen Closure"
  3. Concatenation.
  4. |

### Regular Definition Rules:

* We can give names to regular expressions, and we can use these names as symbols to define other regular expressions.
* A regular definition is a sequence of the definitions of the form:
  ` d 1 => r 1  
    d 2 => r 2  
    .  
    d n => r n  
  `

Examples:

1. Identifiers in Pascal

  ` letter => A | B | ... | Z | a | b | ... | z
    digit => 0 | 1 | ... | 9
    id => letter (letter | digit )\*
  `
2. Identifiers in C

  ` letter => [A-Za-z]
    digit => [0-9]
    CID => letter_(letter_|digit)\*
  `
3. Unsigned numbers in pascal

  ` digit => 0 | 1 | ... | 9
    digits => digit +
    opt-fraction => ( . digits ) ?
    opt-exponent => ( E (+|-)? digits ) ?
    unsigned-num => digits opt-fraction opt-exponent
  `

4. Unsigned numbers or floating point numbers in C

  ` digit => [0-9]
    digits => digit+
    number => digits(.digits)?(E[+-]? digits)?
  `

### Finite Automaton:

- There are two types of FA:
  - Deterministic: faster, take more space.
  - Non-deterministic: slower, take less space.
- Deterministic is widely used in lexical analyzer.
- To generate DFA we have two ways:
  - Regular Expression => NFA => DFA
  - Regular Expression => DFA

**I. NFA To DFA:**
* NFA may have Ɛ transitions.
* DFA Does not have Ɛ transitions.
* In DFA, for each symbol a and state s, there is at most one labeled edge a leaving s.
<br>

  *Thomson's Construction:*
  * Used to convert reg. expression to NFA.

  Example:
  <!-- place Example image -->

  * We use the generated NFA is converted then to DFA.

  Example:

  ` S 0 = Ɛ-closure({0}) = {0,1,2,4,7}

    Ɛ-closure(move(S0 ,a)) = Ɛ-closure({3,8}) = {1,2,3,4,6,7,8} = S1
    Ɛ-closure(move(S0 ,b)) = Ɛ-closure({5}) = {1,2,4,5,6,7} = S2

    Ɛ-closure(move(S1 ,a)) = Ɛ-closure({3,8}) = {1,2,3,4,6,7,8} = S1
    Ɛ-closure(move(S1 ,b)) = Ɛ-closure({5}) = {1,2,4,5,6,7} = S2

    Ɛ-closure(move(S2 ,a)) = Ɛ-closure({3,8}) = {1,2,3,4,6,7,8} = S1
    Ɛ-closure(move(S2 ,b)) = Ɛ-closure({5}) = {1,2,4,5,6,7} = S2
  `

  <!-- place image of NFA -->

  ` S0 is the start state of DFA since 0 is a member of S0 ={0,1,2,4,7}
    S1 is an accepting state of DFA since 8 is a member of S1 = {1,2,3,4,6,7,8}
  `

  <!-- place image of DFA -->

**II. DFA Direct Conversion:**

* First we augment the given regular expression by concatenating it with a special symbol #.
* Then each alphabet symbol (plus #) will be numbered (without Ɛ).
* Then, we create a syntax tree for this augmented regular expression.
* In this syntax tree, all alphabet symbols (plus # and the empty string) in the augmented regular expression will be on the leaves, and all inner nodes will be the operators in that augmented regular expression.
* Then compute first set of the root and follow set of each character.


  Example:

  ` (a\|b) * a         convert it to augmented regular expression.
    (a\|b) * a #       then number each alphabet and #

    ( a \| b )* a #
      1   2    3 4    then create syntax tree
  `

    <!-- place image of syntax tree -->

  ` first(root) = {1, 2, 3}
    followpos(1)={1,2,3}
    followpos(2)={1,2,3}
    followpos(3)={4}
    followpos(4)={}

    S1 =firstpos(root)={1,2,3}
    a: followpos(1) and followpos(3) = {1, 2, 3, 4} = S2
    b: followpos(2) = {1, 2, 3} = S1

    S2 = {1, 2, 3, 4}
    a: followpos(1) and followpos(3)={1,2,3,4}=S2
    b: followpos(2) = {1, 2, 3} = S1
  `

  <!-- place imageof DFA -->

**DFA Minimization:**
* partition the set of states into two groups:
  * G1: set of accepting states.
  * G2: set of non-accepting states.

* For each new group G:
  * partition G into subgroups such that states s1 and s2 are in the same group if and only if for all input symbols a, states s1 and s2 have transitions to states in the same group.

  Example:

  <!-- Place image of DFA -->

  ` G1 = {1, 2, 3}  
    G2 = {4}  

    for G1:
         a   b
    1 => 2   3
    2 => 2   3
    ---
    3 => 4   3

    So, divide G1 into {1, 2} and {3}

    for G2:
         a   b
    4 => 2   3

    Resulting DFA
  `

  <!-- place image of minmized DFA -->

### Issues in Lexical Analyzer:
* The lexical analyzer has to recognize the longest possible string.
* the end of a token is normally not defined
* Normally it doesn’t return a comment as a token. So, the comments are only processed by the lexical analyzer, and the don’t complicate the syntax of the language.

## Lecture 3

```
Not Added Yet!
```

## Lecture 4

```
Not Added Yet!
```

## Lecture 5

```
Not Added Yet!
```

## Lecture 6

```
Not Added Yet!
```



## Other resources

- Sheet (Answered by [AlaaOthman](//github.com/AlaaOhman)): [on Google Drive](https://drive.google.com/file/d/1yXkSxJLjOUPgtGgFM6gkJSPVtjMLJnhD/view?usp=drivesdk)
- Textbook: [Compilers Principles Techniques And Tools](http://booksdl.org/get.php?md5=346B2177C8F721EE62872DCAF64B9F85)
- TutorialsPoint(videos on YouTube): [Playlist](https://www.youtube.com/playlist?list=PLWPirh4EWFpGa0qAEcNGJo2HSRC5_KMT6)
- TutorialsPoint(written): [Lectures](https://www.tutorialspoint.com/compiler_design/index.htm)
- Udacity: [Programming Languages](https://www.udacity.com/course/programming-languages--cs262)
  - String patterns
  - Lexical Analysis
  - Grammars
  - Parsing
  - Interpreting
  - and more...
