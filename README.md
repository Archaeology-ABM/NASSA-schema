# NASSA-schema
The schema for formatting NASSA modules (NASSA.yml fields, directory and file structure).

## Module file structure

### Minimum (must have, to pass validation)

```
YYYY-SURNAME-001 (module root)
│   CHANGELOG.txt
│   LICENSE
|   NASSA.yml
│   README.md
│   references.bib
│
└───documentation
│   │   README.md
│   │
│   └───<IMPLEMENTATION LANGUAGE>
│       │   README.md
│   
└───<IMPLEMENTATION LANGUAGE>
    │   moduleShortTitle.<LANGUAGE EXTENSION>
```

### Maximum (can have)

```
YYYY-SURNAME-001 (module root)
│   .gitignore
│   CHANGELOG.txt
│   LICENSE
|   NASSA.yml
│   README.md
│   references.bib
│
└───documentation
│   │   README.md
│   │   designDetails.md
|   │   ...
│   │
│   └───netlogo
│   |   │   README.md
│   |   │   moduleTitle interface.png
│   |   │   ...
│   |
│   └───python
│   |   │   README.md
│   |   │   diagram.png
│   |   │   ...
│   |
│   └───r
│       │   README.md
│       │   pseudoCode.txt
│       │   ...
│   
└───netlogo_implementation
│   │   moduleShortTitle.nlogo
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
```

## NASSA.yml fields

| field                | level | parent          | description                                                                                                                                                                                                                                                                     | type   | format                                                                                                                                                               | mandatory | implemented in nassa-hs | format check implemented in nassa-hs |
| -------------------- | ----- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- | ----------------------- | ------------------------------------ |
| id                   | 0     |                 | Module identification number. Assigned when opening a submission.                                                                                                                                                                                                               | String | <YEAR>-<FIRSTAUTHORSURNAME>-<999> or a hash?                                                                                                                         | true      | true                    | false                                |
| nassaVersion         | 0     |                 | Latest version of the NASSA schema that applies to this module (NASSA.yml fields, directory and file structure).                                                                                                                                                                | String | 1.0.0 (semantic versioning)                                                                                                                                          | true      | false                   | false                                |
| moduleType           | 0     |                 | Whether a algorithm or a submodel (contain modules)                                                                                                                                                                                                                             | String | Algorithm, Submodel                                                                                                                                                  | true      | true                    | true                                 |
| title                | 0     |                 | Module name or title. It must include a useful description of module.                                                                                                                                                                                                           | String | free text, max. 100                                                                                                                                                  | true      | true                    | true                                 |
| moduleVersion        | 0     |                 | Current version identifier. Defaults to "1.0.0" and should increase after every update.                                                                                                                                                                                         | String | 1.0.0 (semantic versioning)                                                                                                                                          | true      | true                    | true                                 |
| contributors         | 0     |                 | List of contributors to the module                                                                                                                                                                                                                                              |        |                                                                                                                                                                      | true      | true                    | true                                 |
| roles                | 1     | contributors    | How this author contributed to the module (specific labels, see "format" column)                                                                                                                                                                                                | Array  | Author, Compiler, Contributor, Copyright Holder, Creator, Thesis Advisor, Translator (https://journal.r-project.org/archive/2012-1/RJournal_2012-1_Hornik~et~al.pdf) | true      | true                    | true                                 |
| name                 | 1     | contributors    | Full name of a contributor                                                                                                                                                                                                                                                      | String | <SURNAME>, <NAME> with no accent marks                                                                                                                               | true      | true                    | true                                 |
| email                | 1     | contributors    | Stable email of a contributor                                                                                                                                                                                                                                                   | String | valid email                                                                                                                                                          | true      | true                    | true                                 |
| orcid                | 1     | contributors    | ORCID number of a contributor                                                                                                                                                                                                                                                   | String | 9999-9999-9999-9999                                                                                                                                                  | false     | true                    | true                                 |
| license              | 0     |                 | Software license for the code in this module                                                                                                                                                                                                                                    | String | free text                                                                                                                                                            | false     | true                    | true                                 |
| lastUpdateDate       | 0     |                 | Date of the last update submitted                                                                                                                                                                                                                                               | Date   | YYYY-MM-DD                                                                                                                                                           | true      | true                    | true                                 |
| description          | 0     |                 | Description of what the module does. It should expand the information already given in the name/title.                                                                                                                                                                          | String | free text                                                                                                                                                            | true      | true                    | true                                 |
| relatedModules       | 0     |                 | List of modules this one is related to (similar, depending on, ...)                                                                                                                                                                                                             | Array  | a valid module id as defined above                                                                                                                                   | false     | true                    | false                                |
| references           | 0     |                 | Literature references                                                                                                                                                                                                                                                           |        |                                                                                                                                                                      | false     | true                    | true                                 |
| bibFile              | 1     | references      | Relative path to a .bib file                                                                                                                                                                                                                                                    | String | path                                                                                                                                                                 | true      | true                    | true                                 |
| moduleReferences     | 1     | references      | References that describe and explain the module, any of its parts, or its original use in a model. This includes public repositories holding models that include the module.                                                                                                    | Array  | a valid citation key from the submission BIBTEX file (.bib)                                                                                                          | false     | true                    | true                                 |
| useExampleReferences | 1     | references      | References citing, describing, or using the module, after it has been published in the NASSA library.                                                                                                                                                                           | Array  | a valid citation key from the submission BIBTEX file (.bib)                                                                                                          | false     | true                    | true                                 |
| domainKeywords       | 0     |                 | Domain-related keywords                                                                                                                                                                                                                                                         |        |                                                                                                                                                                      | false     | true                    | false                                |
| subjects             | 1     | domainKeywords  | Subject keyword(s). Example/recommendation: https://ehrafworldcultures.yale.edu/ehrafe/majorSubjects.do                                                                                                                                                                         | Array  |                                                                                                                                                                      | false     | true                    | false                                |
| regions              | 1     | domainKeywords  | Region keyword(s). Example/recommendation: http://www.geonames.org/                                                                                                                                                                                                             | Array  |                                                                                                                                                                      | false     | true                    | false                                |
| periods              | 1     | domainKeywords  | Period keyword(s). Example/recommendation: https://perio.do/en/                                                                                                                                                                                                                 | Array  |                                                                                                                                                                      | false     | true                    | false                                |
| modellingKeywords    | 0     |                 | Modelling-related keyword(s). Using NASSA ontology: <url placeholder>                                                                                                                                                                                                           | Array  |                                                                                                                                                                      | true      | true                    | false                                |
| programmingKeywords  | 0     |                 | Programming-related keyword(s). Using NASSA ontology: <url placeholder>                                                                                                                                                                                                         | Array  |                                                                                                                                                                      | true      | true                    | false                                |
| implementations      | 0     |                 | List of implementations in different programming languages                                                                                                                                                                                                                      |        |                                                                                                                                                                      | true      | true                    | true                                 |
| language             | 1     | implementations | Programming language                                                                                                                                                                                                                                                            | String | Options: R, Python, Netlogo, Java, Julia, C#, Ruby, Processing                                                                                                       | true      | true                    | true                                 |
| codeDir              | 1     | implementations | Relative path to the directory containing the implementation in this language                                                                                                                                                                                                   | String | path                                                                                                                                                                 | true      | true                    | true                                 |
| softwareDependencies | 0     |                 | Listing any software (libraries, packages, etc), specifying the release version, on which the module relies to properly function.                                                                                                                                               | Array  | free text                                                                                                                                                            | true      | true                    | true                                 |
| inputs               | 0     |                 | List of inputs required by the module. Create entries for each of the variables that can or should be given/set externally, so that the module can work.                                                                                                                        |        |                                                                                                                                                                      | false     | true                    | true                                 |
| name                 | 1     | inputs          | Parameter/variable/file name in the module.                                                                                                                                                                                                                                     | String | free text                                                                                                                                                            | false     | true                    | true                                 |
| type                 | 1     | inputs          | Parameter/variable/file type. Use the programming language specific type.                                                                                                                                                                                                       | String | free text                                                                                                                                                            | false     | true                    | true                                 |
| unit                 | 1     | inputs          | Parameter/variable unit of measurement, if applicable.                                                                                                                                                                                                                          | String | free text                                                                                                                                                            | false     | true                    | true                                 |
| default              | 1     | inputs          | Parameter/variable default value                                                                                                                                                                                                                                                | String | free text                                                                                                                                                            | false     | true                    | true                                 |
| description          | 1     | inputs          | Parameter/variable/file description. Meaning, data structure, or any other relevant information for the procurement and preparation of the input.                                                                                                                               | String | free text                                                                                                                                                            | false     | true                    | true                                 |
| outputs              | 0     |                 | List of outputs generated by the module. Create entries for each of the variables that are suggested as outputs. Ideally, the list should also include any module variable that can be read externally and is the product of module mechanisms (i.e., not equal to the inputs). |        |                                                                                                                                                                      | false     | true                    | true                                 |
| name                 | 1     | outputs         | Variable/object name in the module.                                                                                                                                                                                                                                             | String | free text                                                                                                                                                            | false     | true                    | true                                 |
| type                 | 1     | outputs         | Variable/object type. Use the programming language specific type.                                                                                                                                                                                                               | String | free text                                                                                                                                                            | false     | true                    | true                                 |
| unit                 | 1     | outputs         | Variable/object unit of measurement, if applicable.                                                                                                                                                                                                                             | String | free text                                                                                                                                                            | false     | true                    | true                                 |
| description          | 1     | outputs         | Variable/object description. Meaning, data structure, or any other relevant information for data analysis and interpretation or the use of the output as input in another module.                                                                                               | String | free text                                                                                                                                                            | false     | true                    | true                                 |
| readmeFile           | 0     |                 | Relative path to Readme.md or alike, which contains at least the information specified in the NASSA template (<url placeholder>).                                                                                                                                               | String | path                                                                                                                                                                 | false     | true                    | true                                 |
| docsDir              | 0     |                 | Relative path to the directory containing documentation resources.                                                                                                                                                                                                              | String | path                                                                                                                                                                 | false     | true                    | true                                 |
| designDetailsFile    | 0     |                 | Relative path to the design details file. Recommended NASSA template: <url placeholder>                                                                                                                                                                                         | String | path                                                                                                                                                                 | false     | true                    | true                                 |

(generated with https://kdelmonte.github.io/json-to-markdown-table/)