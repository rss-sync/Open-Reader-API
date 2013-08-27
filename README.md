# Open Reader API

This is the repo for the **[Open Reader API](http://rss-sync.github.io/Open-Reader-API/)** and is built with [nanoc](http://nanoc.ws/).

All submissions are encouraged. To submit a change, [fork this repository](https://github.com/rss-sync/Open-Reader-API/fork), commit your changes and send a [pull request](https://help.github.com/articles/using-pull-requests).

## Making Contributions

Making contributions or changes is easy. Clone this repo, alter the content within the content folder and submit a pull request.

All content is created in plain text using the [Markdown](http://daringfireball.net/projects/markdown/) syntax. The folder structure will define the end url path structure so keep that in mind if new files and folders are added.

The final display on http://rss-sync.github.io/Open-Reader-API is updated as needed manually using nanoc.

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

## Updating the live site

The [live site](http://rss-sync.github.io/Open-Reader-API/) lives in the [gh-pages branch](https://github.com/rss-sync/Open-Reader-API/tree/gh-pages). For convenience the gh-pages branch has been added to the main repo as a Git submodule.

To update the live site, update master locally and run `nanoc compile`. The latest generated output will be in `/output/Open-Reader-API/`.

Move into `/gh-pages` folder, clear it's content with `git rm -r *` and copy the output from the parent folder (`cp -r ../output/Open-Reader-API/ .`). Add all files and commit the changes.

Pushing the gh-branch will update the live site. After a successful push, don't forget to update the master branch so that it's pointer to the submodule will have the proper commit hash stored.
