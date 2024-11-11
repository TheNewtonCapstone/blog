# Blog

Welcome to our blog! 

## How To Post

1. Go to `_posts`
2. Create a new file named as `YYYY-MM-DD-title-of-post.md`
3. Make sure the file starts with:
```
---
title: "<title>"
date: YYYY-MM-DD
categories: [<CAT1>, <CAT2>, <CAT3>]
tags: [<tag1>, <tag2>, <tag3>]     # TAG names should always be lowercase
author: <author_initial>
---
```
4. Write the post in Markdown format!

## How To Add Author

1. Go to `_data/authors.yml`
2. Add a new section like follow, while replacing the <> with your info. The `url` field is for a linkedin page, portfolio, etc.:
  ```
<author_initials>:
  name: <author_full_name>
  url: <author_personal_url>
``` 
3. Commit, create PR and merge!

## Building Locally

For local building instructions checkout the [original Chirpy repository](https://github.com/cotes2020/jekyll-theme-chirpy).
