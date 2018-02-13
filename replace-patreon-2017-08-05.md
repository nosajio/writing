---
title: Replace Your Patreon Page With PayPal and MailChimp
category: "idea"
coverImg: "https://a.nosaj.io/cover--my-patron.jpg"
coverColor: "#9f9f9f"
---

About a week ago, Journalist Tim pool sent out a tweet asking if anybody could help him create a subscriber platform for donors. 

<div class="embed">
  <blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Looking for help setting up a monthly subscriber platform for donors. Send me an email Tim@tagg.ly</p>&mdash; Tim Pool (@Timcast) <a href="https://twitter.com/Timcast/status/890704719840030726">July 27, 2017</a></blockquote>
  <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
</div>

This happened just after Patreon shut down the account of a journalist without prior warning, and it had a domino effect that caused many content creators to consider that Patreon might one day sever ties with them without any warning.

After looking into the work involved in hacking together a Patreon-like page that could be made and hosted with little tech know-how, it became apparent that that Patreon might be easier and cheaper to replace than I had anticipated. So, in the following rough guide I'll show you how to make and host your own subscriber platform that will be resistant to the whims of Silicon Valley.

**The page we'll make will make it possible to do the following:**
- Communicate with potential supporters via text and video.
- Receive support in the form of monthly donations and one-off payments.
- Capture email addresses of new subscribers in MailChimp.

## Prerequisites 
Before we get started you'll need a MailChimp account and a PayPal Business account to make this possible. It also helps if you understand enough HTML to make a simple webpage. [You can open a PayPal business account here](https://www.paypal.com/uk/webapps/mpp/business-updates/business-account), and a [MailChimp account here](https://login.mailchimp.com/signup/?source=website&pid=GAW).

#### Why PayPal
When I started writing this guide, I was set on the idea of using Stripe to handle subscriptions and billing, as they have some nice ways of keeping everything in one place. But as the Stripe solution started to get more complicated, I decided that it wasn't the best approach. The idea of this project is to see if I can easily replace Patreon's core features with web services, and PayPal offer probably the simplest solution out there with their hosted button system.

#### Cost
PayPal don't make it clear how much they charge for using hosted buttons, but it's safe to assume that they will take their usual percentage of 2.9% from each transaction. Patreon's transaction fee is 5%, so this method will give 2.1% back to you per transaction.

## 1: Setup PayPal Subscription Tiers
<div class="image">
  <img src="https://a.nosaj.io/paypal-buttons.jpg" alt="" />
</div>

To receive payments, we'll need to tell PayPal what to charge people when they press on the "Subscribe" button. To do this, [PayPal has a form](https://www.paypal.com/buttons/select) that you can use to setup prices and customise how your button looks.

<div class="image">
  <img src="https://a.nosaj.io/paypal-buttons-code.jpg" alt="" />
</div>

Once your button has been configured, PayPal will generate some code that will need to be pasted into the page that we'll make next. After configuring each button, I pasted the generated code into a empty text file for safe keeping.

## 2: Making the Support Page
<div class="image narrow fill">
  <img src="https://a.nosaj.io/patron-page-timelapse.gif" alt="" />
</div>

<div class="package">
  <p>I've put the code for this on GitHub, and hosted the example page somewhere you can play with it.</p>
  <a href="https://a.nosaj.io/my-patron/index.html" target="_blank" class="link">Example page</a>
  <a href="https://github.com/nosajio/my-patron" target="_blank" class="repo">The code</a>
</div>

This is the most technical part of this guide, and it isn't all that technical, which is a good thing.

I won't go in depth about every part of the page. Instead I'll focus on the important stuff, like how to embed and customise the PayPal buttons, and where to put messaging aimed at potential supporters.

### Making better subscribe buttons
So you might have noticed that PayPal's button tool gives you hideous buttons to work with, but thankfully you also have the option to change the image to one of your own. To add your own button image, change the `<input type="image" src="..." >` tag's `src` attribute to point to the url of your button image.

### Messaging
Patreon has a way of making supporters feel close to creators because of the informal wall-like feature that they call "Posts". As a cheap way to replace this, I've put a section at the top of the page that can be used to either show a message to potential supporters, or even a video similar to YouTube channel's.

## 3: Use MailChimp as a communication channel
One big feature that Patreon offers is the ability to communicate directly with supporters. This can be replicated easily by using MailChimp to collect email addresses of supporters. Once the supporters' addresses are in MailChimp, emails could be sent directly to supporters.

To get supporter's email addresses into MailChimp, PayPal has a system called `Instant Payment Notification` (IPN) that basically works like a webhook that sends a notification to an outside URL every time a sale is made. There's [a excellent guide](http://kb.mailchimp.com/integrations/e-commerce/use-paypal-with-mailchimp) over on MailChimp's knowledge base that I used to get this to work. I recommend reading that guide for more information on plumbing together PayPal and MailChimp.

## Missing Features
My intention with making this guide was to keep it very simple. I just wanted to see if my hunch was correct that Patreon's core features could be made with other tools. I think this guide validates that this is indeed possible. 

Patreon has some other cool features that could be cool to make—maybe in a more in depth guide. One of these features is the mechanism that pays creators only when they release something new, instead of paying them every month. I'm not sure if this pay-per-content feature is liked very much by creators, as I've only heard them complain about it in the past. Instead, the feature appears to be designed for making supporters feel like they are getting their moneys worth. The thing is I only use Patreon as a supporter, so I have to listen to creators when figuring out what is good and what is crappy about Patreon. 

If you have any thoughts on features that could be cool to add to this in the future, you should tweet me [@__nosaj](https://twitter.com/__nosaj).

## There is Hope Beyond Patreon
Replacing Patreon with a custom page is so easy that if I had stakes in Patreon, I'd be a little concerned. I think that Patreon offers a useful service that makes it simple for creators to receive support without worrying about running a complicated platform. But what if running a support platform could actually be easier and cheaper than using Patreon in the long term? There is a lot of potential in this—and if Patreon continue to rock the boat like they have been, we'll no doubt see more people jump ship, and self-hosted solutions like this will no doubt become more common.
