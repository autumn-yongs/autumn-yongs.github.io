---
title: "[CSS] Customize scrollbar on your web browser"
categories: [ HTML/CSS/JS ]
comments: true
---

## Preface

As a new-comer to the blog world who is trying to customize blog by himself, built-in scrollbar provided by browser must be changed.

> This function is only compatible with webkit(or Blink) browser: Chrome, Opera, Safari...  
> If you want to know availability of this function by browser, check 'Browser Compatibility' in this document.
>
> [MDN document: -webkit-scrollbar](https://developer.mozilla.org/en-US/docs/Web/CSS/::-webkit-scrollbar)

## Let's move on!

### 1. CSS Selectors

> You don't have to feel stress from memorizing all of this selectors. It's okay to skip this track and read next part first. And then get back on here later.

* `::-webkit-scrollbar`: the entire scrollbar

* `::-webkit-scrollbar-button`: the buttons on the scrollbar (arrows pointing upwards and downwards).

* `::-webkit-scrollbar-thumb`: the draggable scrolling handle.

* `::-webkit-scrollbar-track`: the track (progress bar) of the scrollbar.

* `::-webkit-scrollbar-track-piece`: the part of the track (progress bar) not covered by the handle.

* `::-webkit-scrollbar-corner`: the bottom corner of the scrollbar, where both horizontal and vertical scrollbars meet.

* `::-webkit-resizer`: the draggable resizing handle that appears at the bottom corner of some elements.

### 2. My code block as an example

```text
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
```

* Scrollbar part of my stylesheets
```css
::-webkit-scrollbar {
	height: 8px; // horizontal scrollbar's height
	width: 5px; // vertical scrollbar's width
} 
::-webkit-scrollbar-track {
	background-color: white;
} 
::-webkit-scrollbar-thumb {
	background-color: dimgray; 
	border-radius: 30px; // I made scrollbar round 
} 
::-webkit-scrollbar-button,
::-webkit-scrollbar-corner {
	display: none;
}
```

* Can you figure out what element is applied where? I'm not sure about my blog's future style, but I hope that you could understand each selector's role.

### 3. How to make scrollbar appear?

* If there's no scrollbar but you want, or vice versa, I recommend you to read this document. It explains css style related to availability of scrollbar.  
[MDN document: overflow](https://developer.mozilla.org/ko/docs/Web/CSS/overflow)

## Reference

* [MDN document: -webkit-scrollbar](https://developer.mozilla.org/en-US/docs/Web/CSS/::-webkit-scrollbar)




