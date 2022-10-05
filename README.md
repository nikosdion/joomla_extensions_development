# Joomla Extensions Development

**The missing Joomla reference for extension developers**

Permission is granted to copy, distribute and/or modify this document under the terms of the GNU Free Documentation License, Version 1.3 or any later version published by the Free Software Foundation; with no Invariant Sections, no Front-Cover Texts, and no Back-Cover Texts. A copy of the license is included in the section entitled "GNU Free Documentation License".

## WORK IN PROGRESS

I am currently in the process of writing this book. Many things are missing, even more need refining.

Please keep in mind that I am writing this book on my own time, without any kind of funding, based on my own experiences developing software for Joomla, _just for the love of the community_. Please be kind.

## How to read this book

An [HTML version of the book](https://www.dionysopoulos.me/book.html) can be found on my personal site.

_The book on the site is kept automatically up-to-date._ Whenever there is a Git push to this repository —manual or by merging a Pull Request— a GitHub Action deploys the DocBook XML source document to my site. A CRON job on my site runs every 10', checking if the file has changed. If it's changed since the last run, [Akeeba DocImport](https://github.com/akeeba/docimport) converts the XML book into HTML and publishes the updated articles. Automation! Mmm!

## “Developing” the book

### Editing the source

The normative source format of this book is DocBook XML version 5+. You can find it in the `joomla_extensions_development.xml` file in this repository.

_Pro tip_: If you want to edit the XML file easily you can use the free version of the [XMLMind DocBook Editor](https://www.xmlmind.com/xmleditor/docbook_editor.html) (Personal Edition License). This kind of use is permitted as this book is distributed under an Open Source license making it an open source project for the purposes of [XMLMind's Personal License](https://www.xmlmind.com/xmleditor/license_xxe_perso.html).

### Proposing changes

If you want to propose changes to the book please submit an issue or make Pull Request against the DocBook XML document. Make sure to check the [contribution guide](.github/CONTRIBUTING.md) first.

### Compiling the book to other formats

The book can be converted to GitHub-flavored Markdown and EPUB formats using [Pandoc](https://pandoc.org) using the following commands:

```bash
pandoc -f docbook -t epub --toc -N joomla_extensions_development.xml -o joomla_extensions_development.epub
pandoc -f docbook -t gfm -s joomla_extensions_development.xml -o joomla_extensions_development.md
```

Note 1: do not try to convert the book to PDF or ePUB with the Personal Edition of XMLMind DocBook Editor. It is designed to duplicate letters in random words of the output document (the converter is just a preview of their commercial offering).

Note 2: conversion to PDF does not currently work as intended. There are text overflow issues in the numerous code samples in the book. I will work on that once the book is nearer towards completion. 