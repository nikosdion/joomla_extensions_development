# Joomla Extensions Development

**The missing Joomla reference for extension developers**

Permission is granted to copy, distribute and/or modify this document under the terms of the GNU Free Documentation License, Version 1.3 or any later version published by the Free Software Foundation; with no Invariant Sections, no Front-Cover Texts, and no Back-Cover Texts. A copy of the license is included in the section entitled "GNU Free Documentation License".

## WORK IN PROGRESS

I am currently in the process of writing this book. Many things are missing, even more need refining.

Please keep in mind that I am writing this book on my own time, without any kind of funding, based on my own experiences developing software for Joomla, _just for the love of the community_. Please be kind.

## How to read this book

Download [the EPUB file](joomla_extensions_development.epub) and open it in your favorite e-book reader.

## “Developing” the book

The normative format of this book is DocBook XML version 5+. You can find it in the `joomla_extensions_development.xml` file in this repository.

If you want to propose changes to the book please make a Pull Request against the DocBook XML document.

The book can be converted to GitHub-flavored Markdown and EPUB formats using [Pandoc](https://pandoc.org) using the following commands:

```bash
pandoc -f docbook -t epub --toc -N joomla_extensions_development.xml -o joomla_extensions_development.epub
pandoc -f docbook -t gfm -s joomla_extensions_development.xml -o joomla_extensions_development.md
```

The first command is what I use to generate the ePUB version you see in this repository.