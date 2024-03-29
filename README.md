---
title: "Presentation slides and report template"
subtitle: "How to make slides and a report with markdown from one source"
author: [Stefan Sobek]
#bibliography: paper.bib
date: "2020-06-10"
subject: "How to make slides and a report with markdown from one source"
keywords: [Fontys, Markdown, Agile]
lang: "en"
titlepage: "true"
logo: "images/fontyslogo.png"
titlepage-rule-color: "400070"
page-background : "images/fontyslogo-background.png"
# reveal settings
# simple black white league beige sky night serif simple solarized blood moon
theme: black
separator: <!-- s -->
verticalSeparator: <!-- v -->
notesSeparator: <!-- n -->
revealOptions:
  # None - Fade - Slide - Convex - Concave - Zoom
  transition: 'slide'
  transition-speed: fast
  slideNumber: true
  history: true
  progress: true
  width: 1248
  height: 800
  parallaxBackgroundImage: 'images/fontys-parallax-all-dark.jpg'
  parallaxBackgroundSize: '2100px 1024px'
  #autoSlide: 4000
  #loop: true

  # center: false
...
---

# Presentation slides and report template

[FontysVenlo/slides-and-report-template: A useful template for making your slides with markdown and revealjs and on top of that create a nice pdf paper with eisvogel template](https://github.com/FontysVenlo/slides-and-report-template)

<!-- s -->

## Why?

- normal presentations are boring<!-- .element: class="fragment fade-up" -->
- still differences in the platforms even in MS power point, e.g. Windows, Mac or Linux, online Power Point.<!-- .element: class="fragment" -->
- Usually you have multiple sources and multiple output documents so not only slides but maybe also papers you would like to provide for the students.<!-- .element: class="fragment" -->
- These papers are currently in pdf form delivered to the students, and can also be simple pdfs of the slides.<!-- .element: class="fragment" -->
- Solution wanted having one single source and decide what to have in the slides and maybe also additional and more detaillled information in a paper as pdf, docx or webpage.<!-- .element: class="fragment" -->

<!-- s -->

## Current solution

[The HTML presentation framework | reveal.js](https://revealjs.com/) presentations.<!-- .element: class="fragment fade-up" -->

- is still tech based (HTML)<!-- .element: class="fragment fade-up" -->
- Now based on Markdown, as simple language<!-- .element: class="fragment fade-up" -->
- Simple to write and support for transforming it into other document types, e.g. with pandoc is pretty good.<!-- .element: class="fragment fade-up" -->

<!-- s -->

## How to use this template

- Use this as template instead of cloning it, so you get rid of all the commits. Click on the template-button near to the cloning option <!-- .element: class="fragment fade-up" -->
  
![Template button](images/template-button.jpg)<!-- .element: class="fragment fade-up" -->

- Now you can create an own repository based on this repository.<!-- .element: class="fragment fade-up" -->

<!-- s -->

## Create a report

- Luckily, it will be done automatically by github actions (due to the [make-pdf.yml file](.github/workflows/make-pdf.yml)) of course<!-- .element: class="fragment fade-up" -->
- If you now click on Actions tab and then on the first build <!-- .element: class="fragment fade-up" -->

![Actions tab](images/actions1.jpg) <!-- .element: class="fragment fade-up" -->

<!-- s -->
- then click on the report.pdf file if the build is green <!-- .element: class="fragment fade-up" -->

![Actions tab](images/actions2.jpg) <!-- .element: class="fragment fade-up" -->

- you will download a PDF which was generated from the README.md file. Nice! <!-- .element: class="fragment fade-up" -->
- How to adapt that see a later chapter. <!-- .element: class="fragment fade-up" -->
  
<!-- s -->  

## Create a presentation

- Now I want a presentation from the same content.
- Prerequisite is having docker installed on your machine.
  - [Get Docker | Docker Documentation](https://docs.docker.com/get-docker/)
- With docker running, first clone your repository to your local machine.

<!-- s -->

- Go into the directory and do the following in a Terminal/Command line:

```bash
docker run --rm -p 1948:1948 -v `pwd`:/slides webpronl/reveal-md:latest
```

![reveal-markdown docker image](images/reveal1.gif)

<!-- s -->

- Now open `http://localhost1948`in your browser.<!-- .element: class="fragment fade-up" -->
- click on the README.md link:<!-- .element: class="fragment fade-up" -->

![README.md](images/reveal2.jpg)<!-- .element: class="fragment fade-up" -->

- HTML Presentation starts!<!-- .element: class="fragment fade-up" -->

![README.md](images/reveal3.jpg)<!-- .element: class="fragment fade-up" -->

<!-- s -->

## Presentation automatically published on Github Pages

- With the deploy-slides.yml file the presentation will be automatically published to github pages.
- Check the settings of your repository, and activate github pages on gh-pages branch
- done! You can access it online via the url which is published there.

- Github repo url: [https://github.com/FontysVenlo/slides-and-report-template](https://github.com/FontysVenlo/slides-and-report-template)
- Will deploy it then on [https://fontysvenlo.github.io/slides-and-report-template](https://fontysvenlo.github.io/slides-and-report-template/)
- Your URL will be similar, you can see that in the settings then.

<!-- v -->

## Further information

### Adapt presentation data

- So you should of course change all the text here in the README.md file and put your own (course) content in here. <!-- .element: class="fragment fade-up" -->
  
<!-- v -->

#### Adapt title, subtitle and more

- to change it you have to change the parameters in the beginning of the document, here a snippet:<!-- .element: class="fragment fade-up" -->

<!-- v -->

```json
...
title: "Presentation slides and report template"
subtitle: "How to make slides and a report with markdown from one source"
author: [Stefan Sobek]
date: "2020-06-10"

...

```

<!-- v -->

- The first options belong to the report, such as title and subtitle. 
- Starting from `# reveal settings` the settings for revealjs begin
- As the pdf report settings are quite self explaining, I will provide some infos for how to change some specific things in the presentation.

<!-- v -->

- theme:
  - choose one theme from the provided presenation themes: # simple black white league beige sky night serif simple solarized blood moon 
- e.g. `theme: simple`

<!-- v -->

![separators](images/reveal4.jpg)

- **separator:** Defines a separator for horizontal slides. Look into this README.md file how this works. If you put this comment into the markdown text, the report will ignore it and revealjs will create a slide page. So you have to define what should be on your slides. 

<!-- v -->

![separators](images/reveal4.jpg)

- **verticalSeparator:** Defines a vertical separator, means that if you put this in the markdown text, then a vertical slide will be created. This means you can navigate with arrow-down on the keyboard to this slide. 
- **HINT** I use this a lot for **hiding** information in slides or provide backup slides or just **hide** stuff in slide so that it is only in the PDF report. Advantage: get the details out of the presentation but still have it available if necessary. Look it up in this README.md code. E.g. this part is also not horizontally visible, thus available on the last slide by going **down**
<!-- v -->
- **notesSeparator:** Defines a separator for speaker notes. The setting currently is: `notesSeparator: <!-- n -->`
If you put `<!-- n -->` somewhere in the text and your speaker notes here, they will not be shown in the slides. Good thing is, these notes will be generated when you generate a pdf-report. 

Example: 

```
## Project Portfolio Management

- Organizations group and manage projects and programs as a portfolio of investments<!-- .element: class="fragment" -->

<!-- n -->
- These Porfolio investments contribute to the entire enterprise’s success
- Portfolio managers help their organizations make wise investment decisions by helping to select and analyze projects from a strategic perspective
```
If you now press the **s** key the speaker notes pop up: 
![speaker notes](images/speaker-notes.jpg)

presentation slide looks like:
![Slide view](images/slide-notes.jpg)


<!-- v -->

- `transition: 'slide'` - set the transition from slide to slide to None - Fade - Slide - Convex - Concave - Zoom 
- `parallaxBackgroundImage: 'images/fontys-parallax-all.jpg'` - nice feature of having a parallax background image, means it moves when going from slide to slide. 
- `autoSlide: 4000` - have your presentation run automatically, 4000 means 4 seconds

### More information and links

- [webpro/reveal-md: reveal.js on steroids! Get beautiful reveal.js presentations from any Markdown file](https://github.com/webpro/reveal-md)
- [The HTML presentation framework | reveal.js](https://revealjs.com/)
- [Präsentationen mit Markdown, reveal.js und Github Pages: mein neuer Workflow – Lost and Found (GERMAN)](https://wittenbrink.net/lostandfound/praesentationen-mit-markdown-reveal-js-und-github-pages-mein-neuer-workflow/)
