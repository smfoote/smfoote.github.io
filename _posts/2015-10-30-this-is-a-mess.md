---
layout: post
title: "This is a Mess"
tags: 52articles web-development technology
comments: true
---
![A really messy desk]({{site.url}}/assets/mess-desk-800.jpg)

I'm going to take a break from writing about my ideas, and instead write about how I feel about the state of front end web development. Based on the title of the article, you might guess that I don't feel so good about it, but that's not entirely true. I'm optimistic about the web, but lately I have felt that the environment that front end developers work in is a big mess. Let me explain.

## The Mess

I have found web development to always be a messy place. Messy hair, messy desks, messy code. Most of this messiness has been, in my opinion, good for us and good for the web. It has allowed us to move quickly and turn the web into something really incredible. The incredible web has changed the way the wold works in significant ways. But recently a new kind of messiness has become a part of the world of web development. This new messiness leads to bizarre bugs, slow development, and hours of frustration. We now live in a world of plugins and packages, addons and modules. Our code is compiled, transpiled, concatenated, "uglified", "browserified", and mangled in many other ways before it gets to the browser. There is so much magic, and so little documentation, and even less error reporting.

## How We Got Here

In 2008, while I was in college, I started building my first website. Though my website had working autocomplete and AJAX form submissions, I did not include a single external library. Everything was vanilla JavaScript. The next year I added jQuery and some library for handling browser history on hash changes (because my website became a single page app). I was probably a few years behind the times (I had no one to tell me otherwise), but that was generally the state of web development not too many years ago. You didn't depend on almost anything except jQuery, and you built everything else on your own.

Today you would be laughed at or frowned at if you said you were going to build a web application without using a framework on the client, a suite of build tools, transpilers for CSS and JavaScript, and a templating engine for HTML. In other words, we rely heavily on code written by people we have likely never met. In theory, that should work fine (it has worked well in many other programming environments).

But we have a culture problem. The problem goes beyond any one company or even geographic location. We become web developers because we love to build things, and the web is a great place to build cool things, quickly. Building things is fun, but explaining how those things work is not nearly as fun. It almost feels like ... work. And our messy-hair, messy-desk lifestyle doesn't look favorably on real work. The first half of our culture problem is that, as a group, we are not good at writing documentation. Many of us started as freelancers or the only developer in our organizations, and in those settings writing documentation just didn't seem as necessary. We weren't writing APIs or libraries or tools being used by other developers&mdash;we were mostly just writing static user interfaces. Writing solid documentation is simply not a part of who we are.

The second half of our culture problem is that we don't like errors. Errors are bad, so we make them red or (worse) we swallow them. It would be terrible to break a user's experience in production with a thrown error, so we write code like this.

<pre><code>try {
  somethingRisky();
} catch (e) {
  // something important should happen in here...
  // oh well, let's move on!
}
</code></pre>

When we were coding alone, error swallowing wasn't a big deal because we knew where the errors might occur and we knew what they meant and how to fix them. Exposing useful error feedback is a skill, and as a group we have not gotten good at it (*ahem* `undefined is not a function` *ahem*).

## Document or it Won't Happen

There is a phrase, originally from the medical profession, that I think applies to web development: "Document or it didn't happen." In the environment we work in now, we use third party code for everything we do. These libraries are supposed to increase the speed with which we can build applications, and in some cases that promise is fulfilled. We take jQuery for granted a lot these days. There's even a website dedicated to letting you know that [you might not need jQuery](http://youmightnotneedjquery.com/). Despite all this talk, jQuery is still a valuable tool that helps web developers work faster and avoid cross-browser bugs. But my favorite feature of jQuery, by far, is the thoroughness of their documentation. Every method and argument is thoroughly explained, usually with multiple examples. I believe this is why jQuery has been successful for so long (also, jQuery [does all things](http://www.doxdesk.com/img/updates/20091116-so-large.gif)).

On the other hand, I have spent days and sometimes weeks trying to build on other frameworks, libraries, and build tools, where documentation is either insufficient or non-existent. I have spent hours searching for blogs and forum posts that will point me in the right direction. I have resorted to reading source code (the worst kind of leaky abstraction is making your users read your source code), and even that did little to help me. The painful truth is, if a framework, library, or tool is not fully documented, you will waste far more time learning to use it than you would save by using it. If it's not documented, it won't happen.

As a group, our culture needs to change. We need to be professionals and produce professional quality software, and that includes documentation. And we need to stop putting up with mediocre software with crappy documentation. If we must be messy, we should be messy elsewhere.

## Where Did I Go Wrong? Seriously, I Need You to Tell Me!

This past week my build was failing. I was guessing that the bug was in my JavaScript, but since my build tools were handling SCSS compilation as well, I really couldn't be sure. Because the error was getting swallowed by some build plugin 3 levels deep. My conversation with my build tool went something like this:

Build-tool: Something went wrong. That's all I can tell you.

Me: Was it a missing semicolon?

Build-tool: No...

Build-tool: Guess again.

Me: Is there something wrong with this new SCSS file?

Build-tool: No...

Build-tool: Well, maybe.

To find the bug, I eventually had to find and edit the error-swallowing code inside my `node_modules` folder to let the actual error through. What a mess. I should never have to edit anything in my `node_modules` folder. One of the most important features of a programming language, library, or tool is error reporting. Admittedly, the bug would have been caught much sooner if the tool I was using had proper documentation. Still, you will make mistakes when writing code, but you shouldn't have to spend all day trying to find your mistakes.

This is the mess we live in, and we're inexplicably okay with it. We put up with new, untested, undocumented code that doesn't tell us what we're doing wrong. We are no longer a group of hobbyists who happen to get paid to practice our hobby. We are professionals and we need professional tools. Others have suggested we [stop pushing the web forward](http://www.quirksmode.org/blog/archives/2015/07/stop_pushing_th.html) or we [choose boring technology](http://mcfunley.com/choose-boring-technology), but I think a progressive web and exciting technologies are great (even essential), so long as they are well built and documented. As web developers we should insist on it from ourselves and from each other.


Thanks to [Prash Jain](https://www.linkedin.com/pub/prayrit-jain/32/bb6/19a) for reviewing this article and taking the photo. Thanks to [Adam Miller](https://www.linkedin.com/in/adammillerlinkedin) for discussing these ideas with me.
