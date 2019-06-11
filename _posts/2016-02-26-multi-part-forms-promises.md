---
layout: post
title: "Handling Multi-step Forms with Promises"
tags: 52articles javascript UI promises
permalink: /blog/multi-part-form-promises
comments: true
---

This week I built a multi-step form at work. The form was tricky because steps could change order or be omitted based on the available data. As I started thinking about how to maintain my sanity while building the form, I kept thinking that [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) were the way to go. It felt right to use Promises, but it took me some serious staring-out-the-window thinking to figure out how to make it work. I'm pretty happy with how it turned out and I'd like to share my process and results.

## How it Works

One of the most common and ubiquitous multi-step forms is the registration form, so I'll use that as an example. Let's say that you are building a registration form with the following steps:

1. Ask for a name and a username
    1. Check that the username is valid and available
2. Ask the user for an email address
    1. Attempt to send a verification code to the email address
3. Ask the user to enter the verification
4. Ask the user to add their Twitter handle
    1. Ping the Twitter API to ensure the Twitter handle exists
5. Save the new user

We will also assume that, if the user is coming from an invite email, the add email step will be skipped (and maybe the name is pre-filled), and if the user is coming from a Twitter link, the add Twitter step can be skipped (I'm not really sure how this would work in practice, but let's say the Twitter link could somehow include the user's verified Twitter handle, for the sake of the example). This sounds like a nightmare to build, with so many logic branches it would a willow weep. Promises to the rescue!

One of the great things about promises is that we can resolve them whenever we want. Chaining promises together and handling errors with `then` and `catch` (or `fail`), respectively, is great for cleaning up callbacks and such, but manually calling `resolve` is even more powerful. Promises aren't just for AJAX, after all. Waiting for a user to submit a form is just as asynchronous as waiting for a server to respond.

In our example, we start a chain of promises, one for each step. First, we show the name-and-username from, and we create an object called `context` and the first promise. When the user submits the first form, we add name and username to the `context` object, and pass `context` to the promise's `resolve` function. The process repeats for each step in the form, until all the data is gathered and we can finally save the new user with all the data saved to `context`.

If the email address is already known, then the `context` object starts with an `email` attribute. When we get to the second promise in the chain, we can check if the `email` attribute is present on `context`. If yes, then we resolve the promise immediately instead of showing the add email form. The same thing applies to the Twitter handle form.

The advantages with this method are that (1) we can treat each step as a separate form, and (2) we can easily skip forms if the data has already been added without creating multiple entry points and logic branches. There is also a third advantage of error handling, which will be discussed below.

## What it Looks Like

A bit of code should help make this method a bit easier to understand.

{% highlight js %}
let multiStepRegistrationForm = {
  init(options) {
    let context = {
      email: options.email;
    };

    this.startFormFlow(context);
  },

  startFormFlow(context) {

    this.getNameAndUsername(context)
        .then(context => this.checkUsernameAvailability(context))
        .then(context => this.getEmailAddress(context))
        .then(context => this.sendVerificationEmail(context))
        .then(context => this.enterVerificationCode(context))
        .then(context => this.getTwitterHandle(context))
        .then(context => this.validateTwitterHandle(context))
        .then(context => this.saveNewUser(context))
        .catch(errContext => this.handleRegErrors(errContext));
  },

  getNameAndUsername(context) {
    return new Promise((resovle, reject) => {
      if (context.name && context.username) {

        // If the data is already there, resolve immediately,
        // moving on to the next step in the promise chain
        resolve(context);
      } else {

        // Show the name-and-username form
        new NameAndUsernameView({
          context,
          resolve,
          reject
        });
      }
    });
  },

  ...

  // The other steps in the chain look a lot like getNameAndUsername
};
{% endhighlight %}

And this is what the view looks like

{% highlight js %}
let NameAndUsernameView = View.extend({
  actions: {
    'submit form': 'handleFormSubmit'
  },

  handleFormSubmit(evt) {
    let context = this.options.context;

    // Excluding form validation for brevity
    context.name = $('#real-name').val();
    context.username = $('#username').val();

    // This is the resolve function from the getNameAndUsername Promise
    this.options.resolve(context);
  },

  ...

  // More view stuff, like init and form validation
});
{% endhighlight %}

## When Things Go Wrong

I was really excited about the simplicity of this method, and especially how cool it was to pass the `resolve` and `reject` methods around to the form views. Until I started testing error cases. Let's say, for example, that your user has completed nearly the whole form, they received the verification email, and they enter the verification code. With a typo. The `enterVerificationCode` Promise will reject, all of the other steps in the chain will be skipped, and `handleRegErrors` will execute. All of the user's work is lost because of one small typo. The Promise is gone, because a promise, once broken, cannot be repaired. This one issue was almost enough to make me give up on the entire method, because, while it's a small issue from the developer's perspective, it's an absolute deal-breaker from the user's perspective. Especially on something like a registration form.

I found a solution from something that was already built into the promise-chain method: if the `email` already exists on the `context`, then immediately resolve the `getEmailAddress` Promise. Each step in the promise chain is just adding some data to the context, so the same check could be used for all of the Promises in the chain, resolving immediately instead of creating and showing the view. When an error occurs, you can start a new promise chain, using the `context` from the failed promise chain. The promises will resolve up to the point where the failure happened, allowing the user to try again without having to start over. The trick is in _how_ you reject the failed promise.

{% highlight js %}

// Usually promises are rejected with just the error, but in this case
// we reject with both the error and the context
reject({
  err,
  context
});
{% endhighlight %}

And now, when you `handleRegErrors`, you can restart the promise chain.

{% highlight js %}
  handleRegErrors(errContext) {
    let {err, context} = errContext;

    if (err) {
      // Show the error to the user
      this.displayError(err);
    }

    if (context) {
      // Restart the promise chain
      this.startFormFlow(context);
    }
  }
{% endhighlight %}

In a few cases, you may need to remove data from the `context` before rejecting the promise. For example, if the entered `username` is not available, you would want to add

```
context.username = null;
```

before calling `reject`.

I have found this method to handle multi-step forms much more simply and intuitively than any other method I've come across. If you know of a better way, or you see a problem with my method, please let me know in the comments.
