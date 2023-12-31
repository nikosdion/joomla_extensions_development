# Joomla Extensions Development

**The missing Joomla reference for extension developers**

Copyright ©2022-2024 Nikolaos Dionysopoulos

Permission is granted to copy, distribute and/or modify this document under the terms of the [GNU Free Documentation License](LICENSE.md), Version 1.3 or any later version published by the Free Software Foundation; with no Invariant Sections, no Front-Cover Texts, and no Back-Cover Texts. A copy of the license is included in the section entitled "GNU Free Documentation License".

## WORK IN PROGRESS

I am currently in the process of writing this book. Many things are missing, even more need refining.

Please keep in mind that I am writing this book on my own time, without any kind of funding, based on my own experiences developing software for Joomla, _just for the love of the community_. Please be kind.

## How to read this book

An [HTML version of the book](https://www.dionysopoulos.me/book.html) can be found on my personal site.

_The book on the site is kept automatically up-to-date._ Whenever there is a Git push to this repository —manual or by merging a Pull Request— a GitHub Action deploys the DocBook XML source documents to my site. A CRON job on my site runs every 10', checking if the file has changed. If it's changed since the last run, [Akeeba DocImport](https://github.com/akeeba/docimport) converts the XML book into HTML and publishes the updated articles. Automation! Mmm!

## “Developing” the book

### Editing the source

The normative source format of this book is DocBook XML version 5+. You can find it in the `joomla_extensions_development.xml` file in this repository.

This file is the “main document”. It has the book metadata and a bunch of [XInclude](https://en.wikipedia.org/wiki/XInclude) statements pulling in the various [chapters](sections) of the document, each one stored as its own, editable file in the `sections` folder.

_Pro tip_: If you want to edit the XML file easily you can use the free version of the [XMLMind DocBook Editor](https://www.xmlmind.com/xmleditor/docbook_editor.html) (Personal Edition License). This kind of use is permitted as this book is distributed under an Open Source license making it an open source project for the purposes of [XMLMind's Personal License](https://www.xmlmind.com/xmleditor/license_xxe_perso.html). Remember that the sections in the main document will appear as non-editable. You will need to edit each individual chapter file separately.

### Proposing changes

If you want to propose changes to the book please submit an issue or make Pull Request against the DocBook XML document. Make sure to check the [contribution guide](.github/CONTRIBUTING.md) first.

### Compiling the book to other formats

The book can be converted to GitHub-flavored Markdown and EPUB formats using the [DocBook XSL](https://github.com/docbook/xslt10-stylesheets/releases) stylesheets and `xsltproc` from the [libxslt](http://www.xmlsoft.org/libxslt/index.html) project.

You can install `libxslt` on Debian-based Linux distributions with
```bash
sudo apt-get install libxslt-dev
```
On Ubuntu you can alternatively use Snap with
```bash
sudo snap install libxslt
```
On macOS you can use the [HomeBrew](https://brew.sh) package manager to install `libxslt` with
```bash
brew install libxslt
```
On Windows you can use the [Chocolatey](https://chocolatey.org) package manager to install `xsltproc` with
```powershell
choco install xsltproc
```

Assuming that `xsltproc` is in your path and the [DocBooc XSL stylesheets](https://github.com/docbook/xslt10-stylesheets) installed in `/opt/docbook-xsl` you can convert the DocBook XML sources to chunked HTML under the directory `/var/www/html/jextdev` with:

```bash
xsltproc --nonet --xinclude --novalid \
  --stringparam body.start.indent 0 \
  --stringparam variablelist.term.break.after 1 \
  --stringparam variablelist.term.separator "" \
  --stringparam variablelist.max.termlength 12 \
  --stringparam section.autolabel 1 \
  --stringparam toc.section.depth 5 \
  --stringparam base.dir /var/www/html/jextdev \
  /opt/docbook-xsl/html/chunkfast.xsl \
  joomla_extensions_development.xml
```

Note 1: do not try to convert the book to HTML, PDF, or ePUB with the Personal Edition of XMLMind DocBook Editor. It is designed to duplicate letters in random words of the output document (the converter is just a preview of their commercial offering).

Note 2: conversion to PDF involves converting the DocBook XML sources to XML:FO and using Apache FOP to convert to PDF. Apache FOP is no longer developed, therefore no effort was spent to optimise the book for PDF export. As a result there are text overflow issues in the numerous code samples in the book which will not be fixed.

Note 3: this repository is not the right place to ask for help about libxslt tools or the DocBook XSL Stylesheets. You're advised to consult [the documentation of DocBook XSL Stylesheets](http://www.sagehill.net/docbookxsl/) and [the man page of `xsltproc`](https://gnome.pages.gitlab.gnome.org/libxslt/xsltproc.html)
