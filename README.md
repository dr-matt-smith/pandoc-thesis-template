pandoc-thesis-template
======================

A template for creating a degree project thesis in markdown + pandoc

## Installing

You need Pandoc and LaTeX installed.

- [Pandoc installation](http://pandoc.org/installing.html)

I also recommend installing Composer, to save pasting that long command at the command line (or make or whatever you prefer ...)

- [Composer installation](https://getcomposer.org/download/)

## Running
If you have Composer installed just type:

    $ composer pdf

If not you need to enter the following at the command line:

    pandoc --latex-engine=xelatex -H preamble.tex -V fontsize=10pt -V documentclass:book -V papersize:a4paper -V classoption:openright --number-sections --bibliography=99_references/references.bib --csl='csl/nature.csl' 00_front_material/1_title.md 00_front_material/2_declaration.md 00_front_material/3_abstract.md 00_front_material/4_acknowledgements.md 05_toc/toc.md 10_chapters/chapter1_introduction/introduction.md 10_chapters/chapter1_introduction/introduction_section2.md 10_chapters/chapter3_extra_results.md 10_chapters/chapter4_generaldiscussion.md 88_appendices/a_meetings/meetings.md 99_references/references.md -o _THESIS.pdf

Of course if you know `make` or can write a Windows `.bat. file, you can put this long command into one of those files too.

If you add a chapter or appendix, then add its name (in the appropriate place in the sequence, e.g. chapter 4 after chapter 3) in the command. That's it!

## References

Add to the collection of references in `/99_references/references.bib`

Only items that are cited will be added to the list of refernces in the generated PDF.

## Citations

To cite a reference item write:

        [@smith2017]

where `smith2017` is the unique 'id' of the reference item.

In a LaTeX BibText reference collection this 'id' comes immediately after the opening brace `{`:

        @article{smith2017,
        author = {Smith, Matt},
        title = {{Some paper about something}},
        journal = {Great papers in compting (Dublin, Ireland)},
        year = {2017},
        volume = {1},
        pages = {1--19}
        }

In a JSON reference collection the 'id' is explicilty named as an 'id' property. In this example the id is `unity_5x_cookbook`:

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

## Further reference

Find some more Pandoc templates here:

- https://github.com/jgm/pandoc/wiki/User-contributed-templates

## Acknowledgements

This thesis template is based on the one publihsed by Chia Kaivalya
https://chiakaivalya.wordpress.com/2014/04/23/using-markdown-pandoc-to-write-my-biology-phd-thesis/

Thanks Chia!