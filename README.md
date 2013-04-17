# Generic Reader API

This is the repo for the **[Generic Reader API](http://rss-sync.github.io/Generic-Reader-API/)** and is built with [nanoc](http://nanoc.ws/).

All submissions are encouraged. To submit a change, fork this repository, commit your changes and send a [pull request](https://help.github.com/articles/using-pull-requests).

## Making Contributions

Making contributions or changes is easy. Clone this repo, alter the content within the content folder and submit a pull request.

All content is created in plain text using the [Markdown](http://daringfireball.net/projects/markdown/) syntax. The folder structure will define the end url path structure so keep that in mind if new files and folders are added.

## Style Guide

Markdown file extensions should be `.md`

A single file should adhere to the following format:

    ---
    title: API Title
    ---

    # API Title

    * TOC
    {:toc}

    ## End point

        [VERB] /path

    ### Parameters

    Parameter 1:
    : - `option 1`: Option 1's definition
      - `option 2`: Option 2's definition

    Parameter 2
    : `option 1`, `option 2`, default: `option 3`

    ### Response

        Example response


## Testing Your Changes

**Note:** Simply changing the Markdown files within `/content` is enough to make contributions or changes to this repo. The following is only for testing.

If you want to test out your changes to ensure the final generation is correct, you can install the `nanoc` gem and `kramdown` gem which is used for Markdown formatting.

view available nanoc commands with:

    nanoc -h

Nanoc compiles the site into static files within the `output` folder. Run the compile with:

    nanoc compile

You can use MAMP or a similar setup to view the resulting files or you can install the `adsf` gem which will work with nanoc. Then you can use:

    nanoc view
    open http://localhost:3000
