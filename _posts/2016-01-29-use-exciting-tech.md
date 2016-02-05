---
layout: post
title: "Use Exciting Technology"
tags: 52articles thoughts technology
comments: true
---

There has been a lot of talk lately about [choosing "boring" technology](http://mcfunley.com/choose-boring-technology) and [technology](http://www.quirksmode.org/blog/archives/2015/07/stop_pushing_th.html) [fatigue](https://www.nczonline.net/blog/2015/09/is-the-web-platform-getting-too-big/). Using new, exciting technology may be fun, but it tends to slow down development in the long run. The [documentation](http://smfoote.com/blog/2015/10/30/this-is-a-mess/) is sparse, the community is small, the solution is incomplete or buggy. In short, exciting technology often ends up being frustrating technology.

Still, I think the emphasis on "boring" technology is somewhat misplaced. If we focus only on stability, we stagnate. If we think only of developer comfort, we become laggards. And when the [innovators and early adopters](https://en.wikipedia.org/wiki/Diffusion_of_innovations) become laggards, what happens to innovation? Someone has to deal with the issues of exciting technology. Usually that someone falls into one of two groups. The first group is the people who can't live without the new technology, so they are forced to deal with its issues. The second group is the people who also can't live without the new technology, but they can't live without it because exciting, new technology is what they live for.

## Making Exciting Technology Great Technology

As software developers, we are lucky that most of the exciting new technology we use is also open source technology with issue trackers and contributing guidelines. We don't just have to get frustrated when things don't work. We can fix them! Of course this isn't always the case, but it sure is empowering when it is.

## When to Use Exciting Technology in Production

Exciting, new technology is not appropriate for every environment, just as boring technology is not always appropriate. If you are building a product for paying customers<sup><a href="#note-1">[1]</a></sup>, stability and reliability are not negotiable. Your product _must_ work. So, when is exciting technology the right choice in such an environment? Why would you use a NoSQL database that has only been around for 5 years over a relational database that has been around decades? Specifically, why did Google start using [Bigtable](https://en.wikipedia.org/wiki/Bigtable)? Sometimes, exciting, new, experimental technology is the only thing that will work<sup><a href="#note-2">[2]</a></sup>. In those cases, exciting tech goes into production and innovation marches forward.

One new browser technology that I find really exciting is [Service Workers](https://jakearchibald.com/2014/offline-cookbook/). This technology has already been deployed by Facebook, Pinterest, and Medium, and yet the browser support is terrible and spec may still change. The useful documentation online is almost entirely limited to [Jake Archibald's blog](https://jakearchibald.com/). The features provided by Service Workers are not critical (we've lived without them for years). So why are all of these big name tech companies using them? Because the non-critical features provided are exactly what users want (faster load times, lower data usage, app-like experiences on the web). Even if a technology may be uncomfortable or frustrating for the developer, if it's what the users want, the extra pain in the [code shouldn't matter](http://smfoote.com/blog/2015/11/06/code-doesnt-matter/).

## When Else to Use Exciting Technology

Some exciting technology is just not fit for your production environment (or, sometimes, any production environment), but that doesn't mean it shouldn't be used at all. Experimenting with new technologies is one of the reasons I have a personal website. I have Google Analytics, and I know that almost no one is visiting smfoote.com, but I enjoy using the site as a place where I can try things out. Last week I made my site work completely offline using Service Workers (I will have to get SSL certs before I can release my offline blog, but again, not many people come to my blog, so I'm not in a huge rush). Using new technologies in personal projects is a great way to kick the tires and find the flaws (and hopefully file the bugs) that will make these technologies fit for production use in the future.

In conclusion, don't use only boring technology. Be courageous and innovate. Be uncomfortable. Get frustrated. Learn. Break things.

<aside id="note-1"><b>Note 1:</b> Users pay with money, time, or both. If you have users, they are paying in some sense. Treat them well.</aside>

<aside id="note-2"><b>Note 2:</b> In my most up-voted [Stack Overflow question](http://stackoverflow.com/questions/3713313/when-should-i-use-a-nosql-database-instead-of-a-relational-database-is-it-okay), I asked when to use a NoSQL database. The answers were all basically, "You'll know when you need it." That has never been the case on any of my personal projects, and I've yet to use one seriously.</aside>
