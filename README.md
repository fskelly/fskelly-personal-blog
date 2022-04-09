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

Logo Attribution
Logo found [here](https://pixabay.com/illustrations/smart-home-house-technology-2769210/)

Image by <a href="https://pixabay.com/users/geralt-9301/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=2769210">Gerd Altmann</a> from <a href="https://pixabay.com/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=2769210">Pixabay</a>

[![Build and deploy Hugo static webpage to Azure blob](https://github.com/fskelly/automate-the-house-blog/actions/workflows/hugoDeploy.yml/badge.svg)](https://github.com/fskelly/automate-the-house-blog/actions/workflows/hugoDeploy.yml)
