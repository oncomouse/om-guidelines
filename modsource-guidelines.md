---
title: Open Modernisms Markdown
---

These guidelines attempt to offer advice for those wishing to contribute documents to the Open Modernisms project. For a file to be easily included in an Open Modernisms anthology, a "master" version of the file must exist in (our slightly specialized) markdown format. Markdown is a simple text markup format that allows one to easily indicate simple divisions and text properties (italics, etc) in plain text. Markdown has a number of advantages for the goals of Open Modernism. Because it is a plain-text format, markdown enables easy version control and editing. Markdown also allows us to use [pandoc](http://pandoc.org), along with a set of customized scripts and templates, to produce a range of output formats (initially HTML and PDF, but conceivably plain text, ePub, TEI, and more), all from a single source.

At the heart of these guidelines are conventions for representing metadata about a text/document (author, title, source) and recommendations for marking up the text itself, with particular attention to the sort of challenges one is likely to encounter in the essays and works at the heart of the Open Modernisms project: challenges of accurately representing poetry, epigraphs, and similar textual features that markdown alone may not easily represent.^[Designed originally as an easier, more economical, way to write HTML, markdown---unlike, for instance, [TEI](www.tei-c.org/)---is not perhaps ideally suited to the challenge of richly remediating print texts. But its advantages (relative simplicity; a universal source format for pandoc) outweigh its lack of descriptive richness. Much of this project represents a tactical attempt to add back in some of the descriptive richness markdown lacks, without too seriously compromising its advantages.] Our markdown, however, is a superset of the pandoc's markdown, so [pandoc's documentation](http://pandoc.org/demo/example9/pandocs-markdown.html) may be valuable as well.

# Metadata

All metadata---information related to a text that is not the body of the text itself (its title, its original publication information, who encoded it)---for an Open Modernisms text is contained at the beginning of the encoded document. This information is encoded as a "[YAML](http://yaml.org/) block" at the very beginning of the file. This YAML metadata block is marked at its beginning and end by three hyphens (`---`) and should include all the metadata for the document: both bibliographical information about the source text (author, title, date, and so on), information about the markdown file (who produced it, from what sources). It may also include an editorial note explaining the text's context/importance/relevance.

Here, for example, is a metadata block for T. S. Eliot's "Tradition and the Individual Talent," originally published in *The Dial* in November of 1923.

```markdown
---
title: '*Ulysses*, Order, and Myth'
author: 
	family: Eliot
	given: T. S.

citation:
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

Note that YAML format consists of key/value pairs (separated by a colon) which can in turn be nested using whitespace. For more information about specific fields, see below.

## Authors

The name of an author is stored as both a family name and a given name. These fields will be used for most purposes in generating output files. 

```markdown
author: 
	given: Charlie
	family: Chaplin
```

<div class='question'>

How should we handle including alternative or commonly abbreviated names. Note in the example above, Eliot's "given" name is "T. S." This seems perverse. We could use brackets in the existing fields, for instance:

```markdown
author:
	given: T. [Thomas] S. [Stearns]
	family: Eliot
	
author:
	given: Charlie [Charles]
	family: Chaplin
```

Or we could try or we could add another field, storing the name in one field and the name to use for most situations in another. For instance:

```markdown
author:
	given: Thomas Sterans
	family: Eliot
	given-use: T. S.
```

</div>

### Dates of Birth and Death

In addition to an author's name, it is possible to include other information about an author. If you wish to include the dates of an author's birth and death, they may be included as `birth` and `death`, in the format `YYYY-MM-DD`. *Memento mori*. 

<div class='question'>

Would we be interested in allowing for author biographies? This could be a short paragraph in the document, or a link to an external file. Linking to an external file might make sense, as it would allow multiple documents to share a single author bio. Can we borrow such bios from a source... maybe REM?

</div>

## Titles

There are two `title` fields in the metadata block, one for the encoded document and another as part of its `citation`. In most cases these two titles will be identical (simply encode the same title in two places). There are instances, however, where the title for a document in the *Open Modernisms* collection would differ from the title of its source text. For instance, if one wished to excerpt a text, one might use its original title in the `citation`, but perhaps provide its title as "Excerpt from "*Ulysses*, Order, and Myth," or similar. Markdown markup (such as *italics*, etc.) can be used in titles. Please keep the title in single quotation marks (this will solve YAML parsing problems that can be caused, for instance, by colons and other punctuation in a title).

## Citation

The `citation` section of the metadata header provides complete citation information about the source of the text of the transcribed document.

The full set of fields that may be included are: 

- `title`: the title of the work as it appears in the source that is being transcribed or represented.

- `container-title`: for works that are part of a larger work---essays in a collection, chapters of a book, articles in a periodical---the `container-title` is the title of the larger item.

- `date`: dates must be encoded as hyphen-separated numbers of the format, `YYYY-MM-DD` or `YYYY-MM` or `YYYY`. This date should reflect the stated publication date in the source document.

- `volume`: for periodical items published with volume information.

- `issue`: for periodical items published with issue information.

- `publisher`: for sources that list a publisher (usually books), this field will container the name of the publisher.

- `publisher-place`: for sources that list the location of publisher, that information can be included here.

- `page`: a page range for the pages on which the essay/article occurs.

## Source

The source is a simple list of resources used to create the document---usually a list of links to electronic resources, image files, or library records of print items consulted for the encoding.

## Responsibility

Be sure to include the name of the person responsible for putting together this transcription file under editor. This field is a list of names; for convenience, also include an email address.

## Note

Any other information about the document or its transcription (including problems with encoding, justifications for edition chosen, and so on) can be included in this note. 

# Transcribing a Document in Markdown

## Headers

By convention we reserve first level headers (i.e. `<h1>`s) for titles of works. If the work you are encoding has subdivisions of some kind, please indicate them using level two headers, encoded in markdown as `##`; if, in turn, those sections are further subdivided use level three headers (`###`) and so on. For consistency, please encode divisions using hashmarks-style headers (so-called "[Atx](http://www.aaronsw.com/2002/atx/intro) Headers")  rather than "underlining" text with hyphens or equals signs (so-called "[Setext](http://docutils.sourceforge.net/mirror/setext.html) Headers.")

**Example**: An essay that had been divided into sections, numbered simply with Roman Numerals, could be encoded:

```markdown
## I

Lorem ipsum, *et cetera*.

## II

Return of the mack...

### III

And so, in conclusion...

```

## Dashes, Non-Roman Characters, and Other Typographical Challenges

### Dashes, Em, En, and Otherwise

Most dashes one encounters are either em-dashes or hyphens. Hyphens may be simply transcribed as is. Em dashes may be transcribed as unicode em-dashes (that is, `—`) or, LaTeX-style, as three hyphens (`---`). The latter encoding may be preferable because it is easier to type in most circumstances and it is easier to proofread.

Should you find yourself confronted by the rare en-dash (`–`), typically used to separate numbers in a range, it may be encoded either with the appropriate unicode character *or* (LaTeX style) with two hyphens.

**Nota Bene**: End of line of hyphenation may be silently removed from a transcription.

### Non-Roman Characters

Usually the easiest way to encode accented or other characters from the extended Latin alphabet is to simply use the appropriate [UTF-8](http://en.wikipedia.org/wiki/UTF-8) character.

## Comments

Comments can be left in markdown using HTML style comments: `<!-- Comments. -->`. Comments will be ignored when the source file is processed and will not appear in the output.

Such comments can be useful as a way of leaving notes or other information in a document that would be valuable to yourself (or someone else working on the encoding). For instance, one could use comments to mark the location of page-breaks in a source image/text. For instance:

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

This encoding, taking a cue from the [TEI guidlines](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-pb.html), marks the location within the running text where the page breaks from 305 to 306. This transcription also roughly respects line breaks, making it easier correlate the transcribed markdown with the source text images. (These line breaks, of course, are ignored by `pandoc` and so disappear when the text is processed to any output format.)

## Poetry

Poetry has particular formatting demands. Marking up poetry requires **two** things: 

1. Individual poetic lines begin with the pipe characters (`|`).
2. The lines must be in a separate `div` with `type='poetry'`.

For instance:

```markdown

Hardy begins his meditation on the Titantic's fate:

<div class='poetry'>

|      In a solitude of the sea
|      Deep from human vanity,
| And the Pride of Life that planned her, stilly couches her.

</div>
```

The whitespace tries to capture the spacing of the origina; this spacing will be preserved in output formats. 

**Note the blank lines---between the `<div class='poetry'>` and the first line of poetry, and the between the last line of poetry and the closing `</div>`.** These are necessary for any `<div>` to be correctly processed by `pandoc`.

## Images

If a document contains an image, you must first obtain a high quality (300dpi or higher) image file of the image, preferably PNG and place it in a the same directory as your markdown file. **Be sure to give the image file a unique filename, relating it to do the file of which it is a part** (something like `[author name]_[essay title]_image_001.png` would work well). To include it in the file, add the following markdown:

```markdown
![](author_essay_image001.png "Optional Short Title of Image")
```

<div class='question'>

Same directory as markdown file, or use one directory per document which can have an `images` subdirectory? How we answer this question affects the scripts we write to build files; right now, in fact, the one thing that prevents from my [current janky set up](https://github.com/c-forster/modsource) from working entirely automatically, is having to manually create an `images` directory for the (one) image (from Ford's "Impression" essay). Not sure if there is an obvious or better way of doing this...

</div>

## Epigraphs

To mark an epigraph please mark it as a `div` of type `epigraph`; this will allow it to be typeset or styled appropriately in output formats. Epigraphs themselves may contain multiple paragraphs, or lines of verse, and should be marked up accordingly. (As with all other `divs`, be sure to include a blank line before both the opening and closing `div` tag.)

**Example**: Consider this page image. ![Title from Richard Aldington's Essay "The Influence of Mr. James Joyce"](aldington_influence-of-james-joyce_title.png)

This material, including complete metadata (with details not available from the image above alone), could be marked up as follows. 

```markdown
---
title: 'The Influence of Mr. James Joyce'
author:
	family: Aldington
	given: Richard
	birth: 1892-07-08
	death: 1962-07-27

bibliography:
	title: 'The Influence of Mr. James Joyce'
	container-title: The English Review
	page: 333-341
	date: 1921-04

sources:
	- http://search.proquest.com/docview/2441624?accountid=14214
 
editor: Chris Forster
---

<div class='epigraph'>

*"La via n'est de soy ny bien ny mal; c'est la place du bien et du mal, selon 
que vous la leur faictes."* --- Montaigne.

</div>

## I

Obviously no valid criticism can be made of Mr. Joyce's 
*Ulysses* until the whole work has been published in book 
form. It seems to me that the serial publication has lasted 
an abnormally long time, and that there s some excuse 
for my impatience in speaking of *Ulysses* while it is 
still fragmentary. Mr. Joyce's attempt is most interesting 
```
