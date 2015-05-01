
# Open Modernisms Markdown

These guidelines attempt to offer advice for those wishing to contribute documents to the Open Modernisms project. For a file to be easily included in an Open Modernisms anthology, a "master" version of the file must exist in our specialized markdown format. Markdown has a number of advantages for the goals of Open Modernism. Because it is a plain-text format, markdown enables easy version control. Markdown also allows us to use [pandoc](http://pandoc.org), along with a set of customized scripts and templates, to produce a range of output formats (initially HTML and PDF, but conceivably plain text, ePub, TEI, and more).

At the heart of these guidelines are conventions for representing metadata about a text/document (author, title, source) and recommendations for marking up the text itself, with particular attention to the sort of challenges one is likely to encounter in the essays and works at the heart of the Open Modernisms project: challenges of accurately representing poetry, epigraphs, and similar textual features that MarkDown may not easily represent.^[Designed originally as an easier, more economical, way to write HTML, markdown---unlike, for instance, [TEI](www.tei-c.org/)---is not perhaps ideally suited to the challenge of richly remediating print texts. But its advantages (relative simplicity; a universal source format for pandoc) outweigh its lack of power.]

## Metadata

All metadata for an Open Modernisms text should be contained in the document itself, encoded as a YAML block at the very beginning of the file. This YAML metadata block should include all the metadata for the document: this includes both bibliographical information about the source text (author, title, date, and so on), information about the MarkDown file (who produced it, from what sources) and can also include an editorial note explaining the text's context/importance/relevance.

Here, for example, is a rather minimal metadata block for T. S. Eliot's "Tradition and the Individual Talent," originally published in *The Dial* in November of 1923.

```markdown
---
title: '*Ulysses*, Order, and Myth'
author: 
	family: Eliot
	given: T. S.

bibliography:
	title: '*Ulysses*, Order, and Myth'
	author:
		family: Eliot
		given: T. S.
	container-title: The Dial
	page: 480-483
	volume: LXXV 
	date: 1923-11

editor: Chris Forster

source:
- http://summit.syr.edu/vwebv/holdingsInfo?bibId=911529
- http://people.virginia.edu/~jdk3t/eliotulysses.htm
- http://onlinebooks.library.upenn.edu/webbin/serial?id=thedial
---
```

Note that both the author and title here appear twice; once for the document, and once in the "bibliography." In most cases, these two fields will likely be identical. Separating them, however, allows us to separate the title for a document in the *Open Modernisms* collection from the title of its source text. For instance, if one wished to excerpt a text, one would use its original title in the `bibliography`, but perhaps provide its title as "Excerpt from "*Ulysses*, Order, and Myth."

The full set of fields that may be included are specified [below](#valid-fields).

### Valid Fields

Below is a noncomprehensive list of valid fields for describing the metadata (both bibliographical and otherwise) as well as some helpful examples.

#### Authors

TK

In addition to a name, other information about an author may be included---date of birth (`birth`) and death (`death`) in the format `YYYY-MM-DD`.

#### Titles

TK

#### Publication Information

TK

#### Bibliography

TK 

## Transcribing a Document in Markdown

TK

### Comments

Comments can be left in markdown using HTML style comments: `<!-- Comments. -->`. Comments will be ignored when the source file is processed and will not appear in the output.

Such comments can be useful to leave information that would be valuable to someone working on the encoding, such as the location of page-breaks. As an example of a such a convention, one might:

```markdown
What facts, then, let us ask ourselves, 
what elements of the spectacle before 
us, will naturally be most interesting to 
a highly developed age like our own, to 
<!-- pb n='306' -->an age making the demand which we 
have described for an intellectual deliverance 
by means of the complete intelligence 
of its own situation?
```

This encoding, for example (taking a cue from the [TEI guidlines](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-pb.html), marks the location within the running text where the page breaks from 305 to 306. This transcription also roughly respects line breaks, making it easier correlate the transcribed markdown with the source text images. (These line breaks, of course, are ignored by `pandoc` and so disappear when the text is processed to any output format.)

### Poetry

TK

### Images

TK

If a document contains an image, you must first obtain a high quality (300dpi or higher) 

### Epigraphs

TK
