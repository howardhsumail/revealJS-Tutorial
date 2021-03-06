# Reveal.js Tutorial

This is a tutorial on utilizing the [reveal.js framework](https://revealjs.com/) with [markdown](https://www.markdownguide.org/) by using the [reveal-md](https://github.com/webpro/reveal-md) tool. Comparing to [Beamer](https://www.overleaf.com/learn/latex/Beamer) which creates PDF slides with TeX, reveal.js creates web-based slides (convertible to PDF) with Javascript + HTML + CSS. A comparison between the two is [here](https://www.maths.dur.ac.uk/users/s.m.fearn/blog/2020/revealjs/). The workflow can be summarized as: edit markdown slides → convert to HTML slides.

🚀 Template is [here](https://www.haochehsu.com/slides/template/index.html). The template markdown file is [here](https://github.com/howardhsumail/revealJS-Tutorial/blob/main/Template/template.md?plain=1).

🚀 Presentation example [demonstration](https://www.haochehsu.com/slides/revealJS/index.html). The example markdown file is [here](https://github.com/howardhsumail/revealJS-Tutorial/blob/main/Example/example.md?plain=1).

### Installation

1. Install Node Version Manager (nvm)

```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
```

2. Load nvm

```shell
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
```

3. Install NodeJS

```shell
nvm install v16
```

4. Install `reveal-md`

```shell
npm install -g reveal-md
```
  
  - Update

    ```shell
    npm i -g reveal-md
    ```
  - Check version
  
    ```shell
    npm view reveal-md version
    ```
    
### Usage

#### Render HTML slides

```shell
reveal-md yourSlides.md --highlight-theme github --static outputFolderName
```

To render the template, [download](https://github.com/howardhsumail/revealJS-Tutorial/archive/refs/heads/main.zip) and unzip the repository. Then direct the workspace to the `Template` folder: `cd <path to Template folder>`. The slides (`index.html` in the output folder) can be rendered by `reveal-md template.md --highlight-theme default output`.

- Theme

  The [choice of themes](https://github.com/hakimel/reveal.js/tree/master/css/theme/source) is defined at line 6 in the markdown file.

- Highlight Theme

  The [choice of highligh-themes](https://github.com/highlightjs/highlight.js/tree/main/src/styles) is defined during rendering.

#### Live view editing

```shell
reveal-md yourSlides.md -w
```

The terminal will return the following message: `Reveal-server started at http://localhost:xxxx`. If the browser does not pop up, paste `http://localhost:xxxx` into the browser to initiate live view.

#### Print PDF slides

Start live viewing and change the URL from `http://localhost:xxxx/<slides>.md#/` to `http://localhost:xxxx/<slides>.md?print-pdf`. Then print the PDF from browser.

### Shortcuts

To control the presentation, press `Shift` + `?` to see keyboard shortcuts. This includes Speaker notes view (`S`), First slide (`Shift` + `←`), Last slide (`Shift` + `→`), Overview (`ESC`), Fullscreen (`F`), and Pause (`B`).

### Markdown editor

We rely on HTML + CSS to control the style and the animations, so [VS Code](https://code.visualstudio.com/) is recommended. For plain markdown files, [Typora](https://typora.io/) is recommended.

---

### Slides

In your working directory, there are 2 files: `markdownSlides.md` and `reveal.json`.

#### 1. `reveal.json`

This is the configuration file. You can specify the `margin`, 4 different page indicators ([options](https://revealjs.com/slide-numbers/)), toggle the visibility of the controller and the bottom progress bar, the `width`, and the `height`.

#### 2. `markdownSlides.md`

Slides are written in markdown ([syntax](https://www.markdownguide.org/basic-syntax/)) with HTML ([syntax](https://www.w3schools.com/html/html5_syntax.asp)) formatting. At the top, you can define the `Title` of the HTML page, background theme ([options](https://revealjs.com/themes/)), slides transition ([options](https://revealjs.com/transitions/)), horizontal slides separator (`---`), and vertical slides separator (`-v-`). To add speaker view notes, use the `Note:` in each slide. Please refer to the [template](https://www.haochehsu.com/slides/template/index.html) for additional syntax.

---

###  Design

In this section, we will go through some common designs. 

#### 1. Fragment

Control each element separately (e.g. display list items sequentially). The declaration is added to each element with `x` being the order:

```md
<!-- .element: class="fragment" data-fragment-index="x" -->
```

Animation can be added to the element by using the following comment:

```md
<!-- .element: class="fragment animationName" -->
```
The `animationName` can be replaced by one of the 17 [effects](https://revealjs.com/fragments/).

#### 2. Transition

The transition between slides in controlled by the following comment:

```md
<!-- .slide: data-transition="transitionName" -->
```
The `transitionName` can be replaced by 6 different [effects](https://revealjs.com/transitions/).

#### 3. Vertical spacing

```html
<div style="margin-bottom:1cm;"></div>
```

#### 4. Alignment

```html
<div style="text-align: left;">
 The contents here including text, images,... will align to left.
</div>
```
More alignment properties can be found [here](https://www.w3schools.com/cssref/pr_text_text-align.ASP).

#### 5. Padding

To re-position, for example, a left-aligned paragraph, we can add paddings:

```html
<div style="padding-left:5cm;">
 Something or another <div></div>
</div>
```
Then the included contents will be shifted to the right by 5cm.

#### 6. Font size and line height

If you find the default font size is too large or the baseline skip is too small, it can be adjusted by the following:

```html
<div style="font-size:25pt; line-height:70px">
 some contents
</div>
```
