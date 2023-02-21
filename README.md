# NASSA-schema
The schema for formatting NASSA modules (NASSA.yml fields, directory and file structure).

## Table of contents

- [NASSA-schema](#nassa-schema)
  - [Table of contents](#table-of-contents)
  - [Module file structure](#module-file-structure)
    - [Minimum (must have, to pass validation)](#minimum-must-have-to-pass-validation)
    - [Maximum (can have)](#maximum-can-have)
  - [NASSA.yml fields](#nassayml-fields)
  - [Programming languages](#programming-languages)
  - [NASSA keywords](#nassa-keywords)
    - [Modelling keywords](#modelling-keywords)
  - [Programming keywords](#programming-keywords)

## Module file structure

### Minimum (must have, to pass validation)

```
YYYY-SURNAME-001 (module root)
│   CHANGELOG.md
│   LICENSE
|   NASSA.yml
│   README.md
│   references.bib
│   
└───<IMPLEMENTATION LANGUAGE>
    └   moduleShortTitle.<LANGUAGE EXTENSION>
```

### Maximum (can have)

```
YYYY-SURNAME-001 (module root)
│   .gitignore
│   CHANGELOG.md
│   LICENSE
|   NASSA.yml
│   README.md
│   references.bib
│
└───documentation
│   │   tableOfContents.md
│   │   designDetails.md
|   │   ...
│   
└───netlogo_implementation
│   │   moduleShortTitle.nlogo
│   │
│   └───documentation
│   |   │   tableOfContents.md
│   |   │   instructions.md
│   |   │   moduleTitle interface.png
│   |   │   ...
│   │
│   └───input
│   │   │   aDataset.csv
│   │   │   aRaster.png
|   |   |   ...
│   │
│   └───output (for demonstration purposes)
│       │   aDataset.csv
│       │   aRaster.png
|       |   ...
│
└───python_implementation
│   │   moduleShortTitle.py
│   │   demonstration.ipynb
|   |   ...
│   |
│   └───documentation
│   |   │   tableOfContents.md
│   |   │   instructions.md
│   |   │   diagram.png
│   |   │   ...
│   │
│   └───input
│   │   │   aDataset.csv
│   │   │   aRaster.png
|   |   |   ...
│   │
│   └───output (for demonstration purposes)
│       │   aDataset.csv
│       │   aRaster.png
|       |   ...
│
└───r_implementation
│   │   moduleShortTitle.r
│   │   demonstration.Rmd
│   │   demonstration.html
│   │   demonstration.md
|   |   ...
│   |
│   └───documentation
│   |   │   tableOfContents.md
│   |   │   instructions.md
│   |   │   pseudoCode.txt
│   |   │   ...
|   |
│   └───demonstration_files
│   │   │   unnamed-chunk-5-1.png
|   |   |   ...
|   |
│   └───input
│   │   │   aDataset.csv
│   │   │   aRaster.png
|   |   |   ...
|   |
│   └───output (for demonstration purposes)
│       │   aDataset.csv
│       │   aRaster.png
|       |   ...
|
|   ... (other implementations)
```

## NASSA.yml fields

| field                | level | parent          | description                                                                                                                                                                                                                                                                     | type   | format                                                                                                                                                               | mandatory |
| -------------------- | ----- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- |
| id                   | 0     |                 | Module identification number. Assigned when opening a submission.                                                                                                                                                                                                               | String | YEAR-FIRSTAUTHORSURNAME-999                                                                                                                                          | true      |
| nassaVersion         | 0     |                 | Latest version of the NASSA schema that applies to this module (NASSA.yml fields, directory and file structure).                                                                                                                                                                | String | 1.0.0 (semantic versioning)                                                                                                                                          | true      |
| moduleType           | 0     |                 | Whether a algorithm or a submodel (contain modules)                                                                                                                                                                                                                             | String | Algorithm, Submodel                                                                                                                                                  | true      |
| title                | 0     |                 | Module name or title. It must include a useful description of module.                                                                                                                                                                                                           | String | free text, max. 100                                                                                                                                                  | true      |
| moduleVersion        | 0     |                 | Current version identifier. Defaults to "1.0.0" and should increase after every update.                                                                                                                                                                                         | String | 1.0.0 (semantic versioning)                                                                                                                                          | true      |
| contributors         | 0     |                 | List of contributors to the module                                                                                                                                                                                                                                              |        |                                                                                                                                                                      | true      |
| roles                | 1     | contributors    | How this author contributed to the module (specific labels, see "format" column)                                                                                                                                                                                                | Array  | Author, Compiler, Contributor, Copyright Holder, Creator, Thesis Advisor, Translator (https://journal.r-project.org/archive/2012-1/RJournal_2012-1_Hornik~et~al.pdf) | true      |
| name                 | 1     | contributors    | Full name of a contributor                                                                                                                                                                                                                                                      | String | SURNAME, NAME with no accent marks                                                                                                                                   | true      |
| email                | 1     | contributors    | Stable email of a contributor                                                                                                                                                                                                                                                   | String | valid email                                                                                                                                                          | true      |
| orcid                | 1     | contributors    | ORCID number of a contributor                                                                                                                                                                                                                                                   | String | 9999-9999-9999-9999                                                                                                                                                  | false     |
| license              | 0     |                 | Software license for the code in this module                                                                                                                                                                                                                                    | String | free text                                                                                                                                                            | false     |
| lastUpdateDate       | 0     |                 | Date of the last update submitted                                                                                                                                                                                                                                               | Date   | YYYY-MM-DD                                                                                                                                                           | true      |
| description          | 0     |                 | Description of what the module does. It should expand the information already given in the name/title.                                                                                                                                                                          | String | free text                                                                                                                                                            | true      |
| relatedModules       | 0     |                 | List of modules this one is related to (similar, depending on, ...)                                                                                                                                                                                                             | Array  | a valid module id as defined above                                                                                                                                   | false     |
| references           | 0     |                 | Literature references                                                                                                                                                                                                                                                           |        |                                                                                                                                                                      | false     |
| moduleReferences     | 1     | references      | References that describe and explain the module, any of its parts, or its original use in a model. This includes public repositories holding models that include the module.                                                                                                    | Array  | a valid citation key from the submission BIBTEX file (.bib)                                                                                                          | false     |
| useExampleReferences | 1     | references      | References citing, describing, or using the module, after it has been published in the NASSA library.                                                                                                                                                                           | Array  | a valid citation key from the submission BIBTEX file (.bib)                                                                                                          | false     |
| domainKeywords       | 0     |                 | Domain-related keywords                                                                                                                                                                                                                                                         |        |                                                                                                                                                                      | false     |
| subjects             | 1     | domainKeywords  | Subject keyword(s). Example/recommendation: https://ehrafworldcultures.yale.edu/ehrafe/majorSubjects.do                                                                                                                                                                         | Array  |                                                                                                                                                                      | false     |
| regions              | 1     | domainKeywords  | Region keyword(s). Example/recommendation: http://www.geonames.org/                                                                                                                                                                                                             | Array  |                                                                                                                                                                      | false     |
| periods              | 1     | domainKeywords  | Period keyword(s). Example/recommendation: https://perio.do/en/                                                                                                                                                                                                                 | Array  |                                                                                                                                                                      | false     |
| modellingKeywords    | 0     |                 | Modelling-related keyword(s). Using NASSA schema specifications.                                                                                                                                                                                                                | Array  |                                                                                                                                                                      | true      |
| programmingKeywords  | 0     |                 | Programming-related keyword(s). Using NASSA schema specifications.                                                                                                                                                                                                              | Array  |                                                                                                                                                                      | true      |
| implementations      | 0     |                 | List of implementations in different programming languages                                                                                                                                                                                                                      |        |                                                                                                                                                                      | true      |
| language             | 1     | implementations | Programming language                                                                                                                                                                                                                                                            | String | Options: 'C#', 'Java', 'Julia', 'NetLogo', 'Processing', 'Python', 'R', 'Ruby'.                                                                                      | true      |
| softwareDependencies | 1     | implementations | Listing any software (libraries, packages, etc), specifying the release version, on which the module implementation relies to properly function.                                                                                                                                | Array  | free text                                                                                                                                                            | true      |
| docsDir              | 0     |                 | Relative path to the directory containing general module documentation.                                                                                                                                                                                                         | String | path                                                                                                                                                                 | false     |
| inputs               | 0     |                 | List of inputs required by the module. Create entries for each of the variables that can or should be given/set externally, so that the module can work.                                                                                                                        |        |                                                                                                                                                                      | false     |
| name                 | 1     | inputs          | Parameter/variable/file name in the module.                                                                                                                                                                                                                                     | String | free text                                                                                                                                                            | false     |
| type                 | 1     | inputs          | Parameter/variable/file type. Use the programming language specific type.                                                                                                                                                                                                       | String | free text                                                                                                                                                            | false     |
| unit                 | 1     | inputs          | Parameter/variable unit of measurement, if applicable.                                                                                                                                                                                                                          | String | free text                                                                                                                                                            | false     |
| default              | 1     | inputs          | Parameter/variable default value                                                                                                                                                                                                                                                | String | free text                                                                                                                                                            | false     |
| description          | 1     | inputs          | Parameter/variable/file description. Meaning, data structure, or any other relevant information for the procurement and preparation of the input.                                                                                                                               | String | free text                                                                                                                                                            | false     |
| outputs              | 0     |                 | List of outputs generated by the module. Create entries for each of the variables that are suggested as outputs. Ideally, the list should also include any module variable that can be read externally and is the product of module mechanisms (i.e., not equal to the inputs). |        |                                                                                                                                                                      | false     |
| name                 | 1     | outputs         | Variable/object name in the module.                                                                                                                                                                                                                                             | String | free text                                                                                                                                                            | false     |
| type                 | 1     | outputs         | Variable/object type. Use the programming language specific type.                                                                                                                                                                                                               | String | free text                                                                                                                                                            | false     |
| unit                 | 1     | outputs         | Variable/object unit of measurement, if applicable.                                                                                                                                                                                                                             | String | free text                                                                                                                                                            | false     |
| description          | 1     | outputs         | Variable/object description. Meaning, data structure, or any other relevant information for data analysis and interpretation or the use of the output as input in another module.                                                                                               | String | free text                                                                                                                                                            | false     |

(generated with https://kdelmonte.github.io/json-to-markdown-table/)

## Programming languages

These are the programming languages currently specified:

| Language name to be used in the NASSA.yml file | Directory name for the respective implementation |
|------------------------------------------------|--------------------------------------------------|
| C#                                             | `csharp_implementation`                          |
| Java                                           | `java_implementation`                            |
| Julia                                          | `julia_implementation`                           |
| NetLogo                                        | `netlogo_implementation`                         |
| Processing                                     | `processing_implementation`                      |
| Python                                         | `python_implementation`                          |
| R                                              | `r_implementation`                               |
| Ruby                                           | `ruby_implementation`                            |

## NASSA keywords

### Modelling keywords

```
initialisation
|
└───agent initialisation
└───grid initialisation
└───time initialisation
└───parameter initialisation
└───variable initialisation
    └───spatial data input
    └───temporal data input
```

```
runtime
|
└───agent
|   └───agent variables
|   └───agent behaviour (self)
|   └───agent behaviour (other)
|   └───agent behaviour (grid)
└───grid
|   └───grid variables
|   └───grid behaviour (self)
|   └───grid behaviour (other)
|   └───grid behaviour (grid)
└───world
    └───scheduler
    └───time
    └───stochasticity
    └───calculation
    └───interface
```

```
experiment
|
└───output
|   └───output formatting
|   └───output summary 
|   └───output visualisation
|   └───output exporting
|   └───output testing
└───data analysis
|   └───data importing
|   └───data preparation
|   └───statistics
|   └───data visualisation
└───experiment design
    └───stop condition
    └───parameter exploration
    └───event schedulling
    └───batch management
```

## Programming keywords

Classification based on ["Comparison of programming paradigms" at Wikipedia.org](https://en.wikipedia.org/wiki/Comparison_of_programming_paradigms). Please note that the goal is not to keep a bullet-proof classification, but to help in querying relevant information from the module library.

```
Action

Array-oriented

Automata-based

Concurrent computing
|
└───Actor-based
└───Choreographic programming
└───Multitier programming
└───Relativistic programming
└───Structured concurrency

Data-driven

Declarative (contrast: Imperative)
|
└───Functional
|   └───Functional logic
|   └───Purely functional
└───Logic
|   └───Abductive logic
|   └───Answer set
|   └───Concurrent logic
|   └───Functional logic
|   └───Inductive logic
|
└───Constraint
|   └───Constraint logic
|       └───Concurrent constraint logic
|
└───Dataflow
|   └───Flow-based
|   └───Reactive
|       └───Functional reactive
└───Ontology
└───Query language

Differentiable

Dynamic/scripting

Event-driven

Function-level (contrast: Value-level)
└───Point-free style
    └───Concatenative

Generic

Imperative (contrast: Declarative)
└───Procedural
└───Object-oriented

Intentional

Language-oriented
└───Domain-specific

Literate

Natural-language programming

Metaprogramming
└───Automatic
|   └───Inductive programming
└───Reflective
|   └───Attribute-oriented
└───Macro
└───Template

Non-structured (contrast: Structured)
└───Array

Nondeterministic

Parallel computing
└───Process-oriented

Probabilistic

Quantum

Set-theoretic

Stack-based

Structured (contrast: Non-structured)
└───Block-structured
└───Object-oriented
|   └───Agent-oriented
|   └───Class-based
|   └───Concurrent
|   └───Prototype-based
|   └───By separation of concerns:
|       └───Aspect-oriented
|       └───Role-oriented
|       └───Subject-oriented
└───Recursive

Symbolic

Value-level (contrast: Function-level)
