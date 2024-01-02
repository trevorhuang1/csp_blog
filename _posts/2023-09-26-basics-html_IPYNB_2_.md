---
layout: post
hide: True
title: Basics of HTML Guide
description: An introduction to basic HTML, and resources to learn more.
type: hacks
permalink: /basics/html
---

{% include nav_basics.html %}

# How does HTML work?
Similar function to Markdown, syntax defines how stuff should be displayed
- HTML is based on beginning and closing tags `<tagname>content</tagname>`
  - Note the "/" on the ending or closing tag of the pair

## Compare markdown to html below
This below example shows comparison of a [heading](https://www.w3schools.com/html/html_headings.asp) and [paragraph](https://www.w3schools.com/html/html_paragraphs.asp).  Click on links to see many more HTML examples.


```python
%%markdown

### Markdown: This is a Heading

This is a paragraph

```



### Markdown: This is a Heading

This is a paragraph




```python
%%html

<h3>HTML: This is a Heading</h3>
<p>This is a paragraph.</p>
```



<h3>HTML: This is a Heading</h3>
<p>This is a paragraph.</p>



# Attributes
- Learn about [attributes](https://www.w3schools.com/html/html_attributes.asp) 
- Tags can have additional info in the form of attributes
- Attributes usually come in name/value pairs like: name="value"

```html
<tagname attribute_name="attribute_value" another_attribute="another_value">inner html text</tagname>
```

- href example with attribute for web link and inner html to describe link

```html
<a href="https://www.w3schools.com/html/default.asp">Visit W3Schools HTML Page</a>
```

## Sample Markdown vs HTML Tags
Image Tag - Markdown

```md
![describe image](link to image)
```

Image Tag - HTML

```html
<!-- no content so no end tag, width/height is optional (in pixels) -->
<img alt="describe image" src="link to image" width="100" height="200">
```

Link Tag - Markdown

```md
[link text](link)
```

Link Tag - HTML

```html
<a href="link">link text</a>
```

Bolded Text - Markdown

```md
**Bolded Text**
```

Bolded Text - HTML

```md
<strong>Bolded Text</strong>
```

Italic Text - Markdown

```md
*Italic Text*
```

Italic Text - HTML

```md
<i>Italic Text</i>
```

# More tags (not really in markdown)
P tag (just represeants a paragraph/normal text)

```html
<p>This is a paragraph</p>
```

Button

```html
<button>some button text</button>
```

Div (groups together related content)

```html
<!-- first information -->
<div>
    <!-- notice how tags can be put INSIDE eachother -->
    <p>This is the first paragarph of section 1</p>
    <p>This is the second paragraph of section 1</p>
</div>

<!-- second information -->
<div>
    <!-- notice how tags can be put INSIDE eachother -->
    <p>This is the first paragarph of section 2</p>
    <p>This is the second paragraph of section 2</p>
</div>
```



# Resources
- https://www.w3schools.com/html/default.asp
- I will show a demo of how to find information on this website

# HTML Hacks
- Below is a wireframe for an HTML element you will create. A wireframe is a rough visual representation of HTML elements on a page and isn't necessarily to scale or have the exact styling that the final HTML will have. Using the syntax above, try to create an HTML snippet that corresponds to the below wireframe.
- The "a tags" can contain any links that you want

![wireframe for html hacks]({{ site.baseurl }}/images/wireframe.png)


```python
%%html

<html>
  <body>
    <header>
      <div id="titles">
        <h2>Demo Website</h2>
        <h4>A website to host coding projects.</h4>
      </div>
      
    </header>

    <!--paragraph tags-->
    <p>
      <div class="text">
        <span class="paragraph" size=1>This is a sample paragraph</span><br>
        <span class="paragraph"></span><br>
        <span class="sentence" size=2>This is a sentence.</span>
        <br>
        <button id="random-button">Random button</button>
      </div>
    </p>

    <p>
      <div>
        <a href="https://www.w3schools.com/">W3 Schools</a>
        <a href="https://chat.openai.com">ChatGPT</a>
      </div> 
    </p>
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Google_2015_logo.svg/368px-Google_2015_logo.svg.png"/>
    <br>
    <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.computertechreviews.com%2Fwp-content%2Fuploads%2F2020%2F05%2FModern-Web-Design-Trends-1200x675.jpg&f=1&nofb=1"/>
    <br>
    <br>
    
  </body>
</html>
```



<html>
  <body>
    <header>
      <div id="titles">
        <h2>Demo Website</h2>
        <h4>A website to host coding projects.</h4>
      </div>

    </header>

    <!--paragraph tags-->
    <p>
      <div class="text">
        <span class="paragraph" size=1>This is a sample paragraph</span><br>
        <span class="paragraph"></span><br>
        <span class="sentence" size=2>This is a sentence.</span>
        <br>
        <button id="random-button">Random button</button>
      </div>
    </p>

    <p>
      <div>
        <a href="https://www.w3schools.com/">W3 Schools</a>
        <a href="https://chat.openai.com">ChatGPT</a>
      </div> 
    </p>
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Google_2015_logo.svg/368px-Google_2015_logo.svg.png"/>
    <br>
    <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.computertechreviews.com%2Fwp-content%2Fuploads%2F2020%2F05%2FModern-Web-Design-Trends-1200x675.jpg&f=1&nofb=1"/>
    <br>
    <br>

  </body>
</html>




```python
%%js

var randomWordList = [
    'appreciation',
    'baking',
    'banquet',
    'cards',
    'celebration',
    'cooking',
    'family',
    'feast',
    'festival',
    'football',
    'gathering',
    'get-together',
    'gratitude',
    'harvest',
    'overeating',
    'travel',
    'autumn',
    'candles',
    'centerpiece',
    'chrysanthemums',
    'corncob wreaths',
    'cornucopia',
    'dried ears of corn',
    'fall floral arrangements',
    'fall wreath',
    'Native American figurines',
    'leaves',
    'pilgrim figurines',
    'pilgrim hats',
    'pumpkins',
    'scarecrows',
    'turkey figurines',
    'acorn squash',
    'apple cider',
    'apple pie',
    'biscuits',
    'butternut squash',
    'candied carrots',
    'candied yams',
    'corn',
    'corn casserole',
    'corn on the cob',
    'corn salad',
    'cornbread',
    'cranberry sauce',
    'creamed corn',
    'dressing',
    'gravy',
    'green bean casserole',
    'ham',
    'hash browns',
    'hubbard squash',
    'macaroni and cheese',
    'macaroni salad',
    'pumpkin bread',
    'pumpkin pie',
    'roast pumpkin',
    'rolls',
    'stuffing',
    'sweet potato hash',
    'sweet potatoes',
    'three-bean salad',
    'turkey',
  ];
  
  function punctuationGenerator() {
    var punctuation = [".", "?", "!"];
    var punctuationSelector = Math.floor(Math.random() * 3);
    return punctuation[punctuationSelector];
  }
  
  function middleGenerator() { //Next time we can combine this with the function above
    var punctuation = [", ", ": ", "; ", " - "];
    var punctuationSelector = Math.floor(Math.random() * 4);
    return punctuation[punctuationSelector];
  }
  
  function tenPercentChance() {
    var tenPercent = Math.floor(Math.random() * 10);
    return tenPercent;
  }
  
  function sentenceLength() {
    var numberOfWords = Math.floor(Math.random() * (10 - 7) + 7)
    return numberOfWords;
  }
  
  //Generates one sentence.
  function sentenceGenerator(sentenceSize) {
    var randomSentence = "";
    if (sentenceSize == null) {
      sentenceSize = sentenceLength();
      // console.log(sentenceSize);
    }
      
    for (var i = 0; i < sentenceSize; i++) {
      var wordSelector = Math.floor(Math.random() * randomWordList.length);
      var word = randomWordList[wordSelector];
      var seperator = " ";
      if (tenPercentChance() == "0"){
              seperator = middleGenerator();
      }
      if (i == sentenceSize - 1) { //last word
        randomSentence += word;
      }
      else if (i == 0){ //first word
        randomSentence += word[0].toUpperCase() + word.slice(1) + seperator;
      }
      else {
        randomSentence += word + seperator;
      }
    }
    //return the sentence
    return randomSentence + punctuationGenerator() + " ";
  }
  
  //Generates a paragraph made up of sentences.
  function paragraphGenerator(paragraphSize) {
    //TODO: This should be using the sentenceGenerator we made to create the sentences for the paragraph.
    var randomParagraph = "";
    if (paragraphSize == null) {
      paragraphSize = Math.floor(Math.random() * (5 - 3) + 3);
    }
    // console.log(paragraphSize);
    for (var i = 0; i < paragraphSize; i++) {
      randomParagraph += sentenceGenerator();
    }
    //return the paragraph
    return randomParagraph;
  }
  
  // console.log("Sentence: " + sentenceGenerator());
  // console.log("Paragraph: " + paragraphGenerator(10));
  
  //document: variable that points to the HTML that is using this javascript
  //querySelectorAll(): finds all elements in the HTML that match the search question
  //forEach(): do something for everything in the list
  //
  document.querySelectorAll(".sentence").forEach(sentence => sentence.innerText = sentenceGenerator(sentence.getAttribute("size")));
  
  document.querySelectorAll(".paragraph").forEach(paragraph => paragraph.innerText = paragraphGenerator(paragraph.getAttribute("size")));
```


    <IPython.core.display.Javascript object>



```python

```
