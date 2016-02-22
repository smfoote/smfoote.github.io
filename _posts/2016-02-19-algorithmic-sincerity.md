---
layout: post
title: "Algorithmic Sincerity"
tags: 52articles
comments: true
---

![Happy Birthday! It's a cake!](/assets/birthday-cake.jpg)

The other day I was trying to figure out why I don't use Facebook to wish my friends happy birthday. It's not because I don't have any friends (good guess, though), and it's not because I don't like birthday celebrations, and it's not because I'm just a big grouch. While I was vacuuming the other night, I realized that I could easily write a program that would automatically send birthday wishes to all my friends on their birthdays, and assuming I don't get too tangled up in the Facebook API, I could probably have the whole thing working in less than a day. Facebook even has automatically generated "Friends Lists", so I could limit my automatic birthday wishes to only "close friends."

## The (Pseudo) Code

For those who are curious how this would work, here is some fake code that would handle sending birthday messages to my friends. This code would automatically be run every day in a [cron job](https://en.wikipedia.org/wiki/Cron).

<pre><code>
// My birthday messages
let BIRTHDAY_MESSAGES = [
                          'Happy Birthday!!!',
                          'Hope you have an awesome day!',
                          'Have fun. You deserve it!'
                        ];

// The id of my close friends list. I don't want to automatically wish
// strangers happy birthday.
let closeFriendsListId = 1234;

// Call the Facebook API
FB.api(
  `/${closeFriendsList}/members`,

  // Handle the response
  (response) => {

    // Make sure the response is good.
    if (response && response.data) {

      // We're going to pretend that toString gives us a nicely formatted date
      let todayString = new Date().toString();

      // Find only the friends who are having a birthday today.
      let bdayFriends = response.data.filter((friend) => {
        return friend.birthday === todayString;
      });

      bdayFriends.forEach(sendBirthdayMessage);
    }
  }
)

function sendBirthdayMessage(friend) {
  let messageIndex = Math.rand_between(0, BIRTHDAY_MESSAGES.length - 1);
  let message = BIRTHDAY_MESSAGES[messageIndex];
  FB.api(
    `/send-message/${friend.id}`,
    { message }
  );
}
</code></pre>

I admit, this is quite a bit of code, and, more importantly, it won't work as it's written. But, it's not too far off and I wrote this fake code in less than 15 minutes. Imagine what a good friend I would be, sending birthday messages to all of my close friends, never missing a single one, year after year.

## More, Weaker Edges

<blockquote>You know the night life is just not for me<br>
'Cause all you really need are a few good friends</blockquote>

[The Format](http://www.azlyrics.com/lyrics/format/thefirstsingle.html)

I don't mean for this article to sound cynical. I think Facebook and the other social networks have done a great job at connecting people. I have over 500 connections on LinkedIn and nearly 400 friends on Facebook. The intersection of those two groups is surprising small, which means that I am connected to around 1,000 people through just those two social networks. What's not surprising is how few of those people I know well. Every once in a while I see someone pop up in my feed and I don't just not know them well, I don't even recognize _their name_. Before Facebook and its social media friends hit the scene in the early 2000's, we had fewer, stronger connections or edges. Each relationship required more effort, either through physical presence or hand written correspondence or some combination. Now, each relationship requires less effort, so we can have more of them, but they tend to be weaker.

The birthday message program made me realize how weak many of my connections have become. Many of my friends on Facebook really are good friends, but I don't send them birthday messages on Facebook because it feels to me to be too insincere. I also don't send them messages outside of Facebook because it's too hard, or I forget, or some other reason. Most likely the other reason is that our relationship has gotten weaker due to the neglect that algorithmic sincerity makes possible. I think Facebook and the others are powerful, useful, and worthwhile tools, but left unchecked, I think they tend to make our relationships weaker.
