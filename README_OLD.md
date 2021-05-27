pandoc-thesis-template
======================

this is the OLD readme - if you want to install Pandoc and LaTex on your local machine, rather than use Github action s...


## Installing

You need Pandoc and LaTeX installed.

- [Pandoc installation](http://pandoc.org/installing.html)

- NOTE (Feb 2017): A couple of my students with Windows 10 had issues installing the latest version of Pandoc. But it all works fine with version 1.91.1. So if you had an issue, then try installing that version from the ['releases' download page](https://github.com/jgm/pandoc/releases)

- if you need "unicodemath.sty" - find it here:

    -[https://github.com/dmarconi/Thesis/blob/master/unicode-math.sty](https://github.com/dmarconi/Thesis/blob/master/unicode-math.sty)


I also recommend installing Composer, to save pasting that long command at the command line (or make or whatever you prefer ...)

- [Composer installation](https://getcomposer.org/download/)

## Running
If you have Composer installed just type:

    $ composer pdf

If you prefer JSON format for your list of reference items, the type:

    $ composer json

The only difference between these two Composer scripts (look inside `composer.json`) is the bit about references:

    --bibliography=05_references/references.bib

If not you need to enter the following at the command line:

    pandoc --latex-engine=xelatex -H preamble.tex -V fontsize=10pt -V documentclass:book -V papersize:a4paper -V classoption:openright --number-sections --bibliography=99_references/references.bib --csl='csl/nature.csl' 00_front_material/1_title.md 00_front_material/2_declaration.md 00_front_material/3_abstract.md 00_front_material/4_acknowledgements.md 05_toc/toc.md 10_chapters/chapter1_introduction/introduction.md 10_chapters/chapter1_introduction/introduction_section2.md 10_chapters/chapter3_extra_results.md 10_chapters/chapter4_generaldiscussion.md 88_appendices/a_meetings/meetings.md 99_references/references.md -o _THESIS.pdf

Of course if you know `make` or can write a Windows `.bat. file, you can put this long command into one of those files too.

If you add a chapter or appendix, then add its name (in the appropriate place in the sequence, e.g. chapter 4 after chapter 3) in the command. That's it!

## References

Add to the collection of references in `/99_references/references.bib`

Only items that are cited will be added to the list of refernces in the generated PDF.

## Citations

To cite a reference item write the 'id' of the reference item in square brackets with an '@-at' sign as follows:

    Lots of people have written about how wonderful Pandoc is, for example see [@smith2017].

where in the above `smith2017` is the unique 'id' of the reference item. This would output something like this (if citations mode is Harvard-Limerick):

    Lots of people have written about how wonderful Pandoc is, for example see (Smith 2017).



In a LaTeX BibText reference collection this 'id' comes immediately after the opening brace `{`:

        @article{smith2017,
        author = {Smith, Matt},
        title = {{Some paper about something}},
        journal = {Great papers in compting (Dublin, Ireland)},
        year = {2017},
        volume = {1},
        pages = {1--19}
        }

In a JSON reference collection the 'id' is explicitly named as an 'id' property. In this example the id is `unity_5x_cookbook`:

          {
            "id": "unity_5x_cookbook",
            "title": "Unity 5.x Coobook",
            "type": "book",
            "publisher": "Packt",
            "publisher-place": "UK",
            "author": [
              {
                "family": "Smith",
                "given": "Matt"
              },
              {
                "family": "Queiroz",
                "given": "Chico"
              }
            ],
            "issued": {
              "date-parts": [
                [
                  2015
                ]
              ]
            }
          },


To cite a reference item without the authors' names, but just have the year/alpha bit, prefix the citation with a minus sign, e.g.:

        Smith [-@smith2017] writes about how wonderful Pandoc is.

would output something like this (if citations mode is Harvard):

        Smith (2017) writes about how wonderful Pandoc is.

## URLs for online sources

For JSON references, if you want a URL and accessed date to be included in your list of references entry then:

- add a "URL" and "accessed" 

    - note that `URL` has to be in upper case for it to be recoginsied - no idea why? all the other fields are lower case ...
    
    - e.g.
    
        ```json
        "URL": "https://www.packtpub.com/eu/game-development/unity-2018-cookbook-third-edition",
        "accessed": {
          "date-parts": [[ 2020, 5, 29 ]]
        }
        ```

For BibTeX references then

- add a "url" and "accessed" field

    - e.g.
    
        ```
        @book{smith2018,
            author = {Smith, Matt},
            title = {Unity 2018 Cookbook},
            publisher = {Packt},
            year = {2018},
            url = {https://www.packtpub.com/eu/game-development/unity-2018-cookbook-third-edition},
            accessed = {2020}
        }
        ```

## Figures

Copy the figure image into folder `03_figures`. E.g. copy the `octocat.png` Github image there.

Use the exclamation mark, followed by caption text (in square brackets), and then path to image file (in parentheses round brackets), e.g.:

```
    ![Github's famous 'Octocat'!](03_figures/octocat.png)
```

## Citing numbered figures

You can cite the figure number in the text (to match the automatic figure numbering) by adding a `\label{<label>}` in the figure line, and using `\ref{<label>}` in your text to get the figure number, e.g.:

```
    See Figiure \ref{octocat} to see the famous Github Octocat logo.

    ![Github's famous 'Octocat'! \label{octocat}](03_figures/octocat.png)
```


## Further reference

Find some more Pandoc templates here:

- https://github.com/jgm/pandoc/wiki/User-contributed-templates

## Using BibTeX rather than CSL for reference database

If you prefer, or have an existing Bibtex set of references, you can easily switch from CSL to Bibtex in the `composer.json` scripts

- add your reference entries to the  `references.bib` in the `05_references` directory

- in `composer.json` in this line `--bibliography=05_references/references.json` change the prefix from `.json` to `.bib`

For more about CSL and BibTeX see [README REFS](README_REFS.md)

## Acknowledgements

This thesis template is based on the one published by Chia Kaivalya
https://chiakaivalya.wordpress.com/2014/04/23/using-markdown-pandoc-to-write-my-biology-phd-thesis/

Thanks Chia!

## Write, then refine ...

"First, you catch your fish, then you need to fillet your fish until you serve the finest piece" 
(Claus Toksvig being quoted by daughter Sandi in Willams 2020)

REFERENCES:
Williams, Z. (2020) "Interview with Sandi Toksvig",  The Guardian newspaper, UK, 25 May 2020.
