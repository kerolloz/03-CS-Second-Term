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
: a program that takes a program written in a source language and translates it into an equivalent program in a target language.  

**Techniques** used in compiler design are applicable to many computer science problems.  

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

Each phase transforms the source program from one representation into another.  

They communicate with:
- error handlers.
- the symbol table.

### Lexical Analyzer

> - Puts information about identifiers into the symbol table.
> - Regular expressions are used to describe tokens (lexical constructs).
> - A (Deterministic) Finite State Automaton can be used in the implementation of a lexical analyzer.

<p id="token"></p> <!-- for reference to token on phases of a compiler  -->

A Token
: describes a pattern of characters having same meaning in the source program. (such as identifiers, operators, keywords, numbers, delimiters and so on)

Example:  
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

![parse tree](http://img.c4learn.com/2012/01/Parse-Tree-Syntax-Analysis-in-Compiler-Design.jpg)  
In a parse tree,
* All terminals are at leaves.
* All inner nodes are non-terminals in a CFG.

_syntax of a language_ is specified by a __CFG__ (CFG rules are mostly recursive)  
we use BNF to specify a CFG  

Example:

```
assgstmt   -> identifier := expression
expression -> identifier
expression -> number
expression -> expression + expression
```

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

The result is a syntax-directed translation (Attribute grammars)  

Example:

```
newval := oldval + 12    
```
` The type of the identifier newval must match with type of the expression (oldval+12)`

### Intermediate Code Generation
> The level of intermediate codes is close to the level of machine codes.

Example:

```
newval := oldval * fact + 1
```

:arrow_down:

```
id1 := id2 * id3 + 1
```

Intermediates Codes :arrow_down: (Quadraples)

```assembly
MULT id2,id3,temp1
ADD temp1,#1,temp2
MOV temp2,,id1
```


### Code Optimizer

```assembly
MULT id2,id3,temp1
ADD temp1,#1,id1
```

### Code Generator

Example:  
(assume that we have an architecture with instructions
whose at least one of its operands is a machine register)

```assembly
MOVE id2,R1
MULT id3,R1
ADD #1,R1
MOVE R1,id1
```







## Lecture 2

**Lexical Analyzer:** it reads the source program character by character to produce tokens.<br>

> Normally a lexical analyzer doesn’t return a list of tokens at one shot, it returns a token when the parser asks a token from it.<br><br>

**Tokens:**
- Represents a set of strings described by a pattern.
- Additional information should be held for that specific lexeme. This additional information is called as the attribute of the token.
- Token type and its attribute uniquely identifies a lexeme.
- Regular expression is used to specify tokens.
<br><br>

**Concepts of Languages:**
- Alphabet: set of finite symbols.
- String: sequence of symbols on an alphabet.
- Language: consists of set of strings.
- Operation on Language:
  <ol>
  <li>Concatenation</li>
  <li>Union</li>
  <li>Exponentiation</li>
  <li>Kleen Closure</li>
  <li>Positive Closure</li>
  </ol>
<br><br>

**Regular Expressions:**
  - Used to describe tokens.
  - Normally, they are built up of simpler regular expressions.
  - Regular set: a language denoted by a regular expression.

**Presedence Rules in Regular Expressions:**
1. Parentheses
2. * "Kleen Closure"
3. Concatenation.
4. |

<!--Regular Definition Rules: -->






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
