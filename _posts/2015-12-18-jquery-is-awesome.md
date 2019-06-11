---
layout: post
title: "You May Not Need jQuery, But it's Awesome"
tags: 52articles web-development technology
permalink: /blog/jquery-is-awesome
comments: true
---

I started building websites in 2008, and later that year (or maybe early 2009) I started using jQuery for the first time. For a beginner, jQuery did more than just make building things easier&mdash;it made things possible that I was simply not capable of building before. I loved jQuery, and I didn't even learn about `$.get`, `$.post`, or `$.ajax` until much later (I was still doing all of my XHR by hand in a very ugly way, with ActiveX fallback for Internet Explorer).

Years passed and a lot of jQuery's functionality has become native. One of jQuery's most powerful tools, the sizzle selector, is now available as [`document.querySelector`](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector) and `document.querySelectorAll`. DOM nodes now have a [`classList`](https://developer.mozilla.org/en/docs/Web/API/Element/classList) property, with `add`, `remove`, and `toggle` methods. CSS can do amazing things with [animation](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations) (see also [CSS transitions](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions)). [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) are native and the [fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) makes AJAX much easier to work with. All of this jQuery inspired native functionality has inspired some developers to proclaim that [you might not need jQuery](http://youmightnotneedjquery.com/). I, too, had been seriously considering removing jQuery from my development toolbox until a recent experience.

## jQuery Just Works

On a project I was working on I needed to get the distance from the top of an element to the top of the page. My original approach was to sum up all of the `offsetTop`s of the element and its parents until there were no more parents. My calculation was a bit off, and I wasn't sure why. I Googled for answers and, as is almost inevitable when Googling for JavaScript answers, my search led to me to StackOverflow, which led me to jQuery. At first I thought, "I should read the jQuery source to see how they're doing it." But then I realized I already had jQuery on the page, so I decided to just try to use the jQuery method ([`offset`](http://api.jquery.com/offset/)). It worked perfectly, in all browsers. I shouldn't have been surprised&mdash;I've had the "it just works" experience with jQuery so many times in the past&mdash;but I was surprised. I was surprised to learn that I might still need jQuery, and I was surprised to realize that I might always need jQuery. Because jQuery just works&mdash;every method in every browser&mdash;and it does pretty much everything you might want or need to do with the DOM.

## jQuery Is Thoroughly Documented

One of my favorite things about jQuery has always been [jquery.com](http://jquery.com/), and especially [api.jquery.com](http://api.jquery.com/). The documentation is up-to-date, searchable, and thorough. Every method is documented with explanations and examples. There is no ambiguity about what jQuery does and how to use it. Especially when compared with the newer, so-much-hotter-right-now tools, libraries, and frameworks, jQuery's near-complete lack of bugs and thorough documentation are refreshing; a shining light, showing us what JavaScript libraries can and should be.

The web has changed a lot since jQuery was first released in 2006, but still, you might (always) need jQuery.
