- V 0.5.0: Recovered docsDir field but making the documentation subdirectories not compulsory in file structure. Added more explicit list of programming languages.

- V 0.4.0: Assuming now that subdirectory names and default files (README.md, references.bib) are fixed, so deleted the following fields: bibFile, codeDir, readmeFile, docsDir.

- V 0.3.0: Made the softwareDependencies field specific to each implementation. Added the Keywords section with modelling and programming lists. Added table of contents.

- V 0.2.0: Moved documentation on implementation to inside the implementation directory. In NASSA.yml: specify in 'docsDir' description that it refers to the directory name of both the general and the implementation-specific documentation directories; discarded 'designDetailsFile' field.

- V 0.1.0: First schema consolidated, made compatible with nassa-hs and files in NASSA modules so far