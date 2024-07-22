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
2. Again in custom-styles.scss, we can use the data-theme attribute 

```scss
html[data-theme="leaf"] { @include leaf-theme; }
html[data-theme="hacker"] { @include hacker-theme; }
```