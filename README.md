# reveal.js template

## [reveal.js][3] presentation written in [markdown][4] set up with [fabric][5] & [fabsetup][6]

This presentation shows how to create a reveal.js presentation which will be
set up with the fabric task `setup.revealjs` of fabsetup.


## Technical Details

It is a [reveal.js](http://lab.hakim.se/reveal-js/) presentation which means
that this presentation is a static HTML5 website using a lot of JavaScript and
CSS.

It has been set up with the fabric task [setup.revealjs][4]
([template preview](https://theno.github.io/revealjs_template)) of
[fabsetup](https://github.com/theno/fabsetup).


## Open The Presentation:

Several possibilities exist:


### Open `index.html` Directly

Just open file `index.html` with Firefox:

    firefox index.html

(Does not work with Chromium which does not import the markdown file
`slides.md'.)


### Serve locally

Assure the symbolic links exist required for starting from within the subdir
`reveal.js`:

    ```sh
    ln -snf  ../img  img
    ln -snf  ../index.html  index.html
    ln -snf  ../reveal.js  reveal.js
    ln -snf  ../slides.md  slides.md
    ```

Change into `reveal.js` subdir, update third libs and start the site:

    ```sh
    cd reveal.js
    npm update  # only required once
    npm start
    ```

Open with your browser:

    http://localhost:8000

Note:
* Works better (and smoother) with Chromium than with Firefox
* Speaker Notes and PDF export require Chromeium/Chrome


### Open github.io page

If this repo has its origin master repo at github and githup page is configured
to build from 'master' branch open this URL:
https://theno.github.io/revealjs_template


## Create PDF

You need the URL of the presentation, either served locally or from github.
Then, [use decktape](https://github.com/astefanutti/decktape#usage) decktape:

    ```sh
    cd ~/bin/decktape/active && \
    ./phantomjs decktape.js --size 1280x800  URL  ~/repos/my_presi/my_presi.pdf
    ```
(decktape [install command][5])

Or just print the `slides.md` rendered by github into a PDF:
https://github.com/theno/revealjs_template/blob/master/slides.md


## Update reveal.js Codebase

This does not need to happen often.  From time to time, maybe a year after the
last edit, the presentation needs an update with regards to contents.  Then, a
reveal.js update could be a good idea, too.

Just re-run task `setup.reveal.js` of
[fabsetup](https://github.com/theno/fabsetup):

    ```sh
    cd ~/repos/fabsetup
    git pull  # updating fabsetup suggested

    fab setup.revealjs -H localhost
    ```

When asked for:
* Enter dir of this presentation
* Anwer 'yes' in order to reset (and re-download) reveal.js codebase


[1]: http://lab.hakim.se/reveal-js/
[2]: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
[3]: http://www.fabfile.org/
[4]: https://github.com/theno/fabsetup/blob/master/howtos/revealjs.md
[5]: https://github.com/theno/fabsetup/blob/master/howtos/revealjs.md#create-pdf-of-the-presentation-with-decktape
[6]: https://github.com/theno/fabsetup/
