---
comments: True
layout: post
title: SASS Project Plans
description: Here are the plans for the project on SASS I plan to do
type: plans
---

## Project Idea
My goal is to create a settings page for the porfolio_2025 repository which allows for dynamic changing of the theme from the website. This would not only show the capabilities of SASS, but also serve as a good project to better acquaint myself with the language. Additionally, I plan to improve pre-existing lessons on SASS such as the one on hacks and possibly make another lesson which dives into more advanced aspects for any students that are interested.

## Design
I made a [repl](https://replit.com/@TrevorHuang1/toggle-switches?v=1) to test out toggle switches and for the overall aesthetic of the page. I drew inspiration from the IOS user interface with the toggle switches
![Design](https://github.com/user-attachments/assets/39da281b-0807-494e-80ca-c1fc541fa8c4)

## Research/Thought Process
After some research online, I realized that changing the theme using SASS and Javascript alone was more complicated than I previously thought. However, after researching some jekyll themes online which can toggle between light and dark mode, I think I've found a solution.

1. First, I would make mixins for to import specific themes, such as leaf and hacker (done in custom-styles.scss)

```scss
@mixin leaf-theme {
  @import "minima/leaf/_leaf";
}

@mixin hacker-theme {
  @import "minima/hacker/jekyll-theme-hacker";
}
```
2. During my reseach, I also found a common use of an attribute in default.html files which used a light/dark mode switcher. Data-theme is used to store the site's current theme, which will be useful for later. 

```html
<html lang="{{ page.lang | default: "en" }}" class="html" data-theme="{{ site.theme_config.appearance | default: "auto" }}">
```
3. In here, the mixins for leaf-theme and hacker-theme are included if the data-theme is "leaf" or "hacker", respectively. This will allow for dynamic changing of the theme if the data-theme attribute is altered.
```scss
html[data-theme="leaf"] { @include leaf-theme; }
html[data-theme="hacker"] { @include hacker-theme; }
```
4. Finally, 