Highlighting-Engine and Symbols
-------------------------------

The Highlighting-Engine is based on syntactic **tokens**. Tokens are organized in logical groups, e.g. comments, numbers, keywords.
Each token belongs to a type which is composed of its group and group-number, related to the scheme **group[a-z]{1}number[0-9]{1,2}**. 
E.g. `c4` (group comments, number 5). This type is used to define styles for each syntax-element.

To provide a language-coherent appearance, each token type has only to be used for its specific purpose!

### Comments ###

Prefix: **c**

* **c0** | Single Line Comments/General
* **c1** | Multi Line Block Comments
* **c2** | Multi Line Doc Comments
* **c9** | Special Comment Syntax

### Keywords ###

Prefix: **k**

* **k0** | Global Keywords
* **k1** | Control Structure Keywords
* **k2** | Variable/Type Initialization Keyword
* **k3** | Operators
* **k4** | Directives
* **k5** | Types
* **k6** | Labels/Symbols
* **k7** | Variable
* **k8** | Type Qualifiers/Modifier
* **k9** | Special Keywords
* **k10** | Namespaces

### Expressions/Literals ###

Prefix: **e**

* **e0** | Boolean Expressions
* **e1** | Null Expressions
* **e2** | Regular Expressions
* **e3** | Constants
* **e4** | Shell/Command Expression

### Strings ###

Prefix: **s**

* **s0** | General Strings
* **s1** | Characters
* **s2** | Template Strings
* **s3** | Template String Delimiter
* **s4** | String Escape Sequences
* **s5** | Multi Line Strings

### Numbers ###

Prefix: **n**

* **n0** | Floats/General Numbers
* **n1** | Integers
* **n2** | Hexadecimal
* **n3** | Binary
* **n4** | Octal
* **n5** | Complex/Imaginary Numbers

### Methods/Functions ###

Prefix: **m**

* **m0** | General/Global Function Calls
* **m1** | General/Dynamic Method Calls
* **m2** | Static Method Calls
* **m3** | Properties

### Generic ###

Prefix: **g**

* **g0** | Generic Symbols 
* **g1** | Brackets

### Language Specific ###

Prefix: **x**

* **x1** | XML Tag
* **x2** | XML Attribute
* **x10** | CSS ID Selector
* **x11** | CSS Class Selector
* **x12** | CSS Rule/Property
* **x13** | CSS Units
* **x14** | CSS Hex Colors
* **x15** | CSS Pseudo Elements/Selectors

### Text Documents ###

Prefix: **t**

* **t0** | Metadata
* **t1** | Heading
* **t2** | Section
* **t3** | Hyperlink
* **t4** | Emphasis/Formatting
* **t5** | OK/Positive (e.g. diff+)
* **t6** | Failure/Negative (e.g. diff-)
* **t7** | Quotes/Blockquotes
* **t8** | Code (not highlighted)