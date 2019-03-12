![Tclssg](./logo/tclssg-logo-text-small.png)

[![Build Status](https://travis-ci.org/tclssg/tclssg.svg)](https://travis-ci.org/tclssg/tclssg)

Tclssg is a static site generator with template support written in Tcl for dbohdan.com. It is intended to make it easy to manage a small to medium-sized website with an optional blog, "small to medium-sized" meaning one with under about 2000 pages. Tclssg uses Markdown for content formatting, [Bootstrap 3](http://getbootstrap.com/docs/3.4/) for layout (with Bootstrap theme support), and Tcl code embedded in HTML for templating.

Features
--------

* [Markdown](#markup), Bootstrap themes, Tcl code for [templates](https://github.com/tclssg/tclssg/wiki/Templating);
* Plain old pages and blog posts [1];
* Footnotes;
* RSS feeds;
* SEO and usability features out of the box: site maps, canonical and previous/next links, `noindex` on collection pages.
* Valid HTML5 and CSS level 3 output;
* Legacy deployment over FTP;
* Deployment over SCP or other protocols with a [custom deployment command](https://github.com/tclssg/tclssg/wiki/Using-deployCustom);
* Support for external comment engines (currently: Disqus);
* Relative links in the HTML output, which make it suitable for viewing over *file://*;
* [Reasonably fast](https://github.com/tclssg/tclssg/wiki/Benchmarks);
* Few dependencies. Experimental self-contained [binaries](https://github.com/tclssg/tclssg/wiki/Binaries) are available for Linux, Windows, and Mac.

1\. A blog post differs from a plain old page in that it has a sidebar with links to other blog posts sorted by recency and tags. The latest blog posts are featured on the blog index and tag pages are generated to collect blog posts with the same tag.

Page screenshot
---------------
![A test page generated by Tclssg](screenshot.png)

Getting started
---------------

Tclssg is known to run on Linux, FreeBSD, OpenBSD, NetBSD, macOS, and Windows 2000/XP/7/8.x/10.

To use it you will need Tcl 8.5 or newer, Tcllib, and SQLite version 3 bindings for Tcl installed.

To install those on **Debian** or **Ubuntu** run the following command:

    sudo apt install tcl tcllib libsqlite3-tcl

On **Fedora**, **RHEL** or **CentOS**:

    su -
    yum install tcl tcllib sqlite-tcl

On **Windows 7 and later** the recommended way to run Tclssg is to install [Magicsplat Tcl/Tk for Windows](https://www.magicsplat.com/tcl-installer/). The copy of Tcl that comes with [Git for Windows](http://msysgit.github.io/) does not include Tcllib or an SQLite 3 module, so it will not run Tclssg out of the box.

On **macOS** use [MacPorts](https://www.macports.org/) or install ActiveTcl for Mac. With MacPorts:

    sudo port install tcllib tcl-sqlite3

Once you have the dependencies installed clone this repository, `cd` into it then run

    chmod +x ssg.tcl
    ./ssg.tcl init
    ./ssg.tcl build --local
    ./ssg.tcl serve --browse

or on Windows

    ssg.cmd init
    ssg.cmd build --local
    ssg.cmd serve --browse

This will create a new website project in the directory `website/` based on the default project skeleton, build the website in `website/output/`, and open the result in your web browser.

Markup
------

Write [Markdown](http://daringfireball.net/projects/markdown/syntax) and use `<!-- more -->` to designate the break between the teaser (the part of the article shown on the blog index and on tag pages) and the rest of the content. Use page settings to customize the page's output. Example:

```markdown
{
    title {Test page}
    blogPost 1
    tags {test {a long tag with spaces}}
    date 2014-01-02
    showDate 0
}
**Lorem ipsum** reprehenderit _ullamco deserunt sit eiusmod_ ut minim in id
voluptate proident enim eu aliqua sit.

<!-- more -->

Mollit ex cillum pariatur anim [exemplum](http://example.com) tempor
exercitation sed eu Excepteur dolore deserunt cupidatat aliquip irure in
fugiat eu laborum est.
```

User's guide
------------

For more information on how to use Tclssg read the **User's guide** on the [project wiki](https://github.com/tclssg/tclssg/wiki).

Answers to frequently asked questions can be found on the [FAQ page](https://github.com/tclssg/tclssg/wiki/FAQ).

License
-------

MIT. See the file [`LICENSE`](LICENSE) for details.

The Tclssg logo images are copyright (c) 2014 dbohdan and are licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

[`skeleton/static/images/placeholder.jpg`](skeleton/static/images/placeholder.jpg) is cropped from a [photo](https://unsplash.com/photos/AsNfzwdcz2I) by Daniel Olah distributed under the [Unsplash license](https://unsplash.com/license).

The [stackato-cli](https://github.com/ActiveState/stackato-cli) browse package is copyright (c) 2011-2012 ActiveState Software Inc. and is distributed under the Apache License, Version 2.0. See [`vendor/browse/license.txt`](vendor/browse/license.txt).

The [Caius](https://github.com/tobijk/caius) Markdown package 1.0 is copyright (c) 2014 Caius Project and is distributed under the MIT license. See [`vendor/markdown/markdown.tcl`](vendor/markdown/markdown.tcl).
