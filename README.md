# Open Modernisms Markdown Guidelines

This repository has a draft of guidelines (recommendations? too strong?) for the "Open Modernisms" project.

I have begun writing the guidelines in markdown; to generate the HTML file that is served at [http://c-forster.github.io/om-guidelines/modsource-guidelines.html](http://c-forster.github.io/om-guidelines/modsource-guidelines.html), simply use pandoc:

`pandoc -S -s --toc --number-section --toc-depth=2 -t html+definition_lists -o modsource-guidelines.html -c style.css modsource-guidelines.md`
