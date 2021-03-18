## Deploying NetlifyCMS on a GitHub Pages site

Site initiated with the help of the [https://github.com/juba/rmdformats](`rmdformats` package).

Steps follow from [here](https://www.netlifycms.org/docs/add-to-your-site/) with some helpful tips from [here](https://cnly.github.io/2018/04/14/just-3-steps-adding-netlify-cms-to-existing-github-pages-site-within-10-minutes.html).

1. Build static page with R Markdown
2. Populate `admin/` with `index.html` (no changes from the template) and `config.yml` (some changes from template in later steps).
3. Generate oAuth App with Netlify at [https://github.com/settings/developers](https://github.com/settings/developers). Application name and homepage URL don't matter, but for Authorization callback URL we need `https://api.netlify.com/auth/done`
4. Set up a new Netlify site from the repo (could actually be from any arbitrary repo, since we're not using Netlify as the host)
5. Go to Netlify Settings -> Domain Management and add `you.github.io` as a custom domain (you can only do this for one site in Netlify!!)
6. Go to Netlify -> Access control and install OAuth provider according to the key in step 3. 
7. Make sure `repo:` and `site_domain:` match your GitHub and Netlify names in `config.yml`. For example: 
```
backend:
  name: github
  repo: tgerke.github.io/netlifyCMS-with-GHPages/
  branch: main
  site_domain: netlifycms-with-ghpages.netlify.com
```