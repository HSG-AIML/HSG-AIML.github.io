---
# Please provide as much information here as possible. If you cannot fill in
# a field, leave it empty. There is no need for quotation marks if your entry
# consists of more than one word.

# list of authors (first name, last name), comma separated
# please put AIML researcher within <strong> XXX </strong> tags
authors:

# date of publication (YYYY-MM-DD)
date:

# leave this as is
layout: post

# title of the publication
title:

# type of publication, please use captitalization (e.g., Journal Paper,
# Conference Poster, Workshop Contribution, ...)
itemtype:

# name of publisher/journal/conference; feel free to add additional
# information like volume number, page number, ...
publisher:

# url to the official publication (could be conference, journal, arxiv)
puburl:

# url to some pdf that is freely accessible (e.g., arxiv)
pdfurl:

# url to code repository (e.g., github)
codeurl:

# url to data repository (e.g., zenodo, github)
dataurl:

# email address of reponsible AIML author
contactemail:

# publication language (e.g., English, German, ...)
language:

# subject areas (keywords); try to cover the following topics:
# - general field (e.g., remote sensing, TTS, financial data, ...)
# - ML method (e.g., deep learning, gradient boosting, supervised learning,
#              semi-supervised learning, self-supervised learning ...)
# - task (e.g, classification, segmentation, representation learning, ...)
subjectareas: 
---

## A Headline

Feel free to use headlines to give your post more structure. Use short paragraphs instead of long texts.

### Year Another Headline

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.


## Figures

You can use figures in your post. You can either add them with simple markdown:

![alt text](/images/AIML-HSG_Logo.png)

or html:

<img src="/images/AIML-HSG_Logo.png" alt="Image"/>

or you can use a template that I wrote to display a centered image with a description:

{% include figure.html
url="/images/AIML-HSG_Logo.png"
description="This is our AIML Logo. It's a good logo. It's the best logo. I have never seen a more beautiful logo." %}

## Creating a new Post

To create a new post, you simply create a new file in `_posts`. Please adhere to the naming conventions: `YYYY-MM-DD-Title_with_whitespaces_filled_with_underscores.markdown`. Please note the combination of dashes and underscores in the filename. The date here and in the meta data of the post have to match, as well as titles.

If you want to use any images in your post, please put them into the directory `images/YYYY-MM-DD-Title_with_whitespaces_filled_with_underscores/`. 


## Checking Your Post Locally

To see the rendering of your post locally, you have to run a jekyll server. You can do so by running `bundle exec jekyll serve` in your local `hsg-aiml.github.io` directory. Before this works, you might have to run `bundle` and `bundle update` in the same directory.

Once the server is running, you can see the rendering in your webbrowser at `localhost:4000`.

For details see [this document](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/testing-your-github-pages-site-locally-with-jekyll).

## Uploading your Posts

Once you are happy with your post, you can simply push it to our github repo (`https://github.com/HSG-AIML/HSG-AIML.github.io`). You have to be a contributor to be able to push directly. Please contact Michael to make you a contributor. Alternatively, you can also fork the repo and then issue a pull request.


If you have any additional questions, please contact Michael.