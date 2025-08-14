- V 1.0.1: Correcting `orcid` as a mandatory field and including a suggestion of using a dummy if the author is absent and does not have one.

- V 1.0.0: Introducing `coverImage` (non-mandatory field), modifying specifications for title and description fields, and adding a section affirming README.md as mandatory and "Further information" as required.

- V 0.5.1: format for `license` must now be a valid SPDX identifier (second column at https://spdx.org/licenses/ ).

- V 0.5.0: Recovered the `docsDir` field, but made the documentation subdirectories non-compulsory in the file structure. Added a more explicit list of programming languages.

- V 0.4.0: Assuming now that subdirectory names and default files (README.md, references.bib) are fixed, so deleted the following fields: `bibFile`, `codeDir`, `readmeFile`, `docsDir`.

- V 0.3.0: Made the softwareDependencies field specific to each implementation. Added the Keywords section with modelling and programming lists. Added table of contents.

- V 0.2.0: Moved documentation on implementation to inside the implementation directory. In NASSA.yml: specify in `docsDir` description that it refers to the directory name of both the general and the implementation-specific documentation directories; discarded `designDetailsFile` field.

- V 0.1.0: First schema consolidated, made compatible with nassa-hs and files in NASSA modules so far
