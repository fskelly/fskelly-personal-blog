# automate-the-house-blog

Backend for my [blog](https://automation.fskelly.com/)

## Create a new post

I like to create my content based upon year  
My folder structure looks like this  
```bash
content  
|---post
    |---year
        |---postTitle.md
```

```bash
hugo new post/{{year}}/{{postTitle}}/index.md
```

![example workflow](https://github.com/fskelly/automate-the-house-blog/actions/workflows/main.yml/badge.svg)
