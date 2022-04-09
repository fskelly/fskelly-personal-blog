# automate-the-house-blog

Backend for my [blog](https://automation.fskelly.com/)

## Create a new post

I like to create my content based upon year  
My folder structure looks like this  
```bash
content  
|---post
    |---year
        |---postTitle
            |---index.md
```

```bash
hugo new post/{{year}}/{{postTitle}}/index.md
```

[![Build and deploy Hugo static webpage to Azure blob](https://github.com/fskelly/automate-the-house-blog/actions/workflows/hugoDeploy.yml/badge.svg)](https://github.com/fskelly/automate-the-house-blog/actions/workflows/hugoDeploy.yml)
