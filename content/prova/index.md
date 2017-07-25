---
date: 2016-03-09T19:56:50+01:00
title: Adding content
weight: 20
---

## Hello world

[link][http://www.google.it]
Let's create our first content file for your documentation. Open a terminal and add the following command for each new file you want to add. Replace `<section-name>` with a general term that describes your document in detail.

# prova2

```sh
hugo new <section-name>/filename.md
```

Visitors of your website will find the final document under `www.example.com/<section-name>/filename/`.

Since it's possible to have multiple content files in the same section I recommend to create at least one `index.md` file per section. This ensures that users will find an index page under `www.example.com/<section-name>`.

## Homepage

To add content to the homepage you need to add a small indicator to the frontmatter of the content file:

```toml
type: index
```

Otherwise the theme will not be able to find the corresponding content file.

## Table of contents

You maybe noticed that the menu on the left contains a small table of contents of the current page. All `<h2>` tags (`## Headline` in Markdown) will be added automatically.

## Admonitions

Admonition is a handy feature that adds block-styled side content to your documentation, for example hints, notes or warnings. It can be enabled by using the corresponding [shortcodes](http://gohugo.io/extras/shortcodes/) inside your content:

```go
{{</* note title="Note" */>}}
Nothing to see here, move along.
{{</* /note */>}}
```

This will print the following block:

{{< note title="Note" >}}
Nothing to see here, move along.
{{< /note >}}

The shortcode adds a neutral color for the note class and a red color for the warning class. You can also add a custom title:

```go
{{</* warning title="Don't try this at home" */>}}
Nothing to see here, move along.
{{</* /warning */>}}
```

This will print the following block:

{{< warning title="Don't try this at home" >}}
Nothing to see here, move along.
{{< /warning >}}

This is a [reference stile link][linkid] to a page. And this [linkid] is also a link. As is [this][] and [THIS].

This is an abbreviation <abbr title="Urban Mobile Cloud Computing">UMCC</abbr> and also this <abbr title="Quality of Service">QoS</abbr>.

[linkid]: http://www.google.it "Optional Title"
[this]: http://www.danielamazza.net "Dani"

*[UMCC]: Urban Mobile Cloud Computing

*[QoS]: Quality of Service

UMCC
QoS
The HTML specification
is maintained by the W3C.

*[HTML]: Hyper Text Markup Language
*[W3C]:  World Wide Web Consortium


I :heart: Hugo!

(@good)  This is a good example.

As (@good) illustrates

(@good)  Another example.

As (@good) also illustrates

Mmark
: A Markdown-superset converter

Black Friday
:     Another Markdown-superset converter

Name    | Age
--------|-----:
Bob     | 27
Alice   | 23


Name    | Age
--------|-----:
Bob     | 27
Alice   | 23
======= | ====
Charlie | 4

|-----------------+------------+-----------------+----------------|
| Default aligned |Left aligned| Center aligned  | Right aligned  |
|-----------------|:-----------|:---------------:|---------------:|
| First body part |Second cell | Third cell      | fourth cell    |
| Second line     |foo         | **strong**      | baz            |
| Third line      |quux        | baz             | bar            |
|-----------------+------------+-----------------+----------------|
| Second body     |            |                 |                |
| 2 line          |            |                 |                |
|=================+============+=================+================|
| Footer row      |            |                 |                |
|-----------------+------------+-----------------+----------------|


<reference anchor='pandoc' target='http://johnmacfarlane.net/pandoc/'>
    <front>
        <title>Pandoc, a universal document converter</title>
        <author initials='J.' surname='MacFarlane' fullname='John MacFarlane'>
            <organization>University of California, Berkeley</organization>
            <address>
                <email>jgm@berkeley.edu</email>
                <uri>http://johnmacfarlane.net/</uri>
            </address>
        </author>
        <date year='2006'/>
    </front>
</reference>

My header {#header}

Lorem ipsum dolor sit amet, at ultricies ...
See Section (#header).

Information can be found on the <https://example.com> homepage.
You can also mail me: <mailto:me@example.com>

{title="The blockquote title"}
{#myid}
> A blockquote with a title

{.go}
    Some code here
