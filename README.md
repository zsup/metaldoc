## Metaldoc [![Build Status](https://travis-ci.org/zsup/metaldoc.svg?branch=master)](https://travis-ci.org/zsup/metaldoc)
=======

Metaldoc is a documentation static site generator, built with Node.js and Metalsmith.

Metaldoc was originally built for [Particle documentation](http://docs.particle.io), which is the best example of Metaldoc in use.

### Installation

To host Metaldoc locally, you'll need Node.js and npm:

    brew install nodejs

Once you have Node.js set up, navigate to this repository's directory on your machine, and then:

    npm install

to install any other necessary dependencies.

### Hosting locally

Metaldoc uses a fabulous tool from the folks at Segment called [Metalsmith](http://www.metalsmith.io). Metalsmith is a static site generator that builds static HTML sites from source material in other formats; in this case, Markdown and Handlebars.

To run a locally hosted version of the documentation, follow the installation instructions above, and then within the 'metaldoc' directory type in your terminal:

`npm start`

This will set up a server running at `http://localhost:8080`. If you make changes to the source content, your browser should automatically refresh using `livereload`.

### Testing

To run the tests locally, run `npm test` from the root of the
repository. This will tell you whether the build will pass on Travis or
not.

### Configuration

Configuration still to be documented, as the current state of this project is that it's still pretty much just set up for Particle Docs.

### Organization

The majority of your content should be stored in the `src/content` directory as a set of Markdown files. Assets such as images and javascript are stored in the `src/assets` directory.

### Structuring your content

Metaldoc will dynamically generate a table of contents for navigation purposes based on the headers (i.e. `###`) that you use on each page. It is important to note that _order and heirarchy matters_ when you are designing the organization of content on your page. Your page should include the following:

* 1 `h1` at the top of the page that will serve as the title of the page. You can even copy the `title` directly from the front-matter of the markdown file like this: `# {{title}}`

* As many `h2`s (`##`) as you'd like to serve as the section headers for the page.

* Underneath every `h2`, if applicable, as many `h3`s (`###`) as you'd like to serve as sub-sections within the section. These will appear as nested within the navigation on the left.

Note that there are only 2 levels of navigation that will appear in the table of contents. *`h4`s and below will not appear in the table of contents*.

### Attributions

This documentation was originally built using [Flatdoc](http://ricostacruz.com/flatdoc/), an awesome tool for building beautiful documentation from simple Markdown files. We have made many modifications since, but the inspiration remains.

### Contributions

aking a contribution is as simple as forking this repository, making edits to your fork, and contributing those edits as a pull request. For more information on how to make a pull request, see [Github's documentation](https://help.github.com/articles/using-pull-requests/).

If you add new features, please add documentation and tests for those features, following the example of existing documentation and tests.

### License

These files have been made available online through a [Creative Commons Attribution-ShareAlike 3.0 license](http://creativecommons.org/licenses/by-sa/3.0/us/).

You are welcome to distribute, remix, and use these files for commercial purposes. If you do so, please attribute the original design to Particle Industries, Inc. both on the website and on the physical packaging of the product or in the instruction manual. All derivative works must be published under the same or a similar license.
