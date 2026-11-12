# kartikangiras.com

Personal website of Kartik Angiras. Plain HTML, CSS and a little JavaScript: no framework, no build step. Open any `.html` file in a browser to preview it, edit it in any text editor, and push to deploy.

## Structure

```
index.html                      Home: intro, links, Work cards
photo.jpg                       Headshot on the home page
og.png                          Link-preview image (LinkedIn, X, WhatsApp)

projects.html                   Projects page
projects/*.jpg                  Project thumbnails

work/*.jpg                      Thumbnails for the home page Work cards
writing/switchai-finance.html   SwitchAI essay, hosted on this site

essays.html                     Short personal essays (empty for now)

reads.html                      Reads: links to STEM, Papers, Books, Videos, Thoughts
reads/stem.html                 Courses and lecture series
reads/books.html                Reading list
reads/videos.html               Talks and interviews

literature-reviews.html                         Papers: list of topics
literature-reviews/machine-learning.html        Machine Learning topic
literature-reviews/machine-learning/*.html      One page per paper review

source-files/pipeline.svg       Editable source of the Milvus pipeline diagram
```

## Common edits

**Add a Work card (home page).** In `index.html`, find `const WORK = [` near the bottom and add an entry:

```js
{ title: "Card title", date: "Dec 2026", cat: "Distributed Systems",
  href: "https://link-to-the-work",
  img: "work/my-image.jpg",            // optional; leave out for a drawn placeholder
  desc: "One or two sentences on what you did." },
```

Thumbnails are cropped to 16:10. Put the image in `work/`.

**Add a project.** Same pattern in `projects.html`, inside `const PROJECTS = [`. Images go in `projects/`. Newest first.

**Edit the intro, bullets or links.** In `index.html`, look for `<ul class="facts">` (bullets), `<p class="about">` (personal line) and `<nav class="socials">` (icon row).

**Add a book, course or video.** In `reads/books.html`, `reads/stem.html` or `reads/videos.html`, copy an existing `<li>` line inside the right `<section>`. To add a new section, copy a whole `<section class="shelf-sec">` block.

**Add a paper review.**
1. Copy `literature-reviews/machine-learning/attention-is-all-you-need.html`, rename it, and replace the text.
2. In `literature-reviews/machine-learning.html`, copy an `<a class="row paper-row">` block and point it at the new file.
3. In `literature-reviews.html`, add the paper to that topic's `papers: [ ... ]` list so the count updates. For a new topic, add an entry to `TOPICS` with its own `href`.

**Add an essay.** Copy `writing/switchai-finance.html` as a template for the page. Then in `essays.html`, add an entry to `const POSTS = [ ]`.

**Change the link underline color.** In `index.html`, edit `--link:` in the `:root` block at the top.

## Link previews

Every page has description, Open Graph and Twitter tags (search for `og:title`). New pages should copy that block from an existing page and update the title, description and URL. To check a preview after deploying, use LinkedIn's Post Inspector or opengraph.xyz.

## Deploy

- **Netlify:** connect this repo, with no build command and `/` as the publish directory. Every push deploys.
- **GitHub Pages:** Settings → Pages → deploy from `main`, root folder.

Then add `kartikangiras.com` as the custom domain and set the DNS records your host shows you.

## Fonts

Text uses ET Book (Edward Tufte's typeface, MIT licensed), loaded from jsDelivr, with Crimson Pro from Google Fonts as a fallback.
