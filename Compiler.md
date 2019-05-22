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

| Phase                                                       | what happens                                                                                                                                                                                                                    |
|:------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Lexical Analyzer](#lexical-analyzer)                       | reads the source program character by character and returns the [tokens](#token) of the source program.                                                                                                                         |
| [Syntax Analyzer](#syntax-analyzer) (parser)                | creates the syntactic structure (generally a parse tree) of the given program.                                                                                                                                                  |
| [Semantic Analyzer](#semantic-analyzer)                     | checks the source program for semantic errors and collects the type information for the code generation.                                                                                                                        |
| [Intermediate Code Generator](#intermediate-code-generator) | produces an explicit intermediate codes representing the source program. These intermediate codes are generally machine (architecture) independent. But the level of intermediate codes is close to the level of machine codes. |
| [Code Optimizer](#code-optimizer)                           | optimizes the code produced by the intermediate code generator in the terms of time and space.                                                                                                                                  |
| [Code Generator](#code-generator)                           | Produces the target language in a specific architecture. The target program is normally is a relocatable object file containing the machine codes.                                                                              |

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

![parse tree](http://img.c4learn.com/2012/01/Parse-Tree-Syntax-Analysis-in-Compiler-Design.jpg)

### Other resources

- Sheet (Answered by [AlaaOthman](//github.com/AlaaOhman)): `Not added yet`
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
