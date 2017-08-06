---
title: Replace Your Patreon Page With PayPal and MailChimp
category: "idea"
coverImg: "http://a.nosaj.io/cover--my-patron.jpg"
coverColor: "#9f9f9f"
---

About a week ago, Journalist Tim pool sent out a tweet asking if anybody could help him create a subscriber platform for donors. 

<div class="embed">
  <blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Looking for help setting up a monthly subscriber platform for donors. Send me an email Tim@tagg.ly</p>&mdash; Tim Pool (@Timcast) <a href="https://twitter.com/Timcast/status/890704719840030726">July 27, 2017</a></blockquote>
  <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
</div>

This happened just after Patreon shut down the account of a journalist without prior warning. This caused many content creators to consider the possibility that Patreon might sever ties with them without any warning.

After looking into the work involved in hacking together a Patreon-like page that could be made and hosted with little tech know-how, it became apparent that that Patreon might be easier and cheaper to replace than I had anticipated. So, in the following rough guide I'll show you how to make and host your own subscriber platform that will be resistant to the whims of Silicon Valley.

The thing we'll make will make it possible to do the following:
- Communicate with potential supporters via text and video.
- Receive support in the form of monthly donations, or one-off payments.
- Capture email addresses of new subscribers in MailChimp.

## Prerequisites 
Before we get started you'll need a PayPal Business account to make this possible. It also helps if you understand enough about HTML to make a simple webpage. [You can open a PayPal business account here](https://www.paypal.com/uk/webapps/mpp/business-updates/business-account).

#### Why PayPal
When I started writing this guide, I was set on the idea of using Stripe to handle subscriptions and billing, as they have some nice ways of keeping everything in one place. But as the Stripe solution started to get more complicated, I decided that it wasn't the best approach. The idea of this project is to see if I can easily replace Patreon's core features with web services, and PayPal offer probably the simplest solution out there with their hosted button system.

#### Cost
PayPal don't make it clear how much they charge for using hosted buttons, but it's safe to assume that they will take their usual percentage of 2.9% from each transaction. Patreon's transaction fee is 5%, so this method will give 2.1% back to recipients per transaction.

## 1: Setup PayPal Subscription Tiers
<div class="image">
  <img src="http://a.nosaj.io/paypal-buttons.jpg" alt="" />
</div>

To receive payments, we'll need to tell PayPal what to charge people when they press on the "Subscribe" button. To do this, [PayPal has a form](https://www.paypal.com/buttons/select) that you can use to setup prices and customise how your button looks.

<div class="image">
  <img src="http://a.nosaj.io/paypal-buttons-code.jpg" alt="" />
</div>

Once your button has been configured, PayPal will generate some code that will need to be pasted into the page that we'll make next. After configuring each button, I pasted the generated code into a empty text file for safe keeping.

## 2: Making the Support Page
<div class="image fill">
  <img src="http://a.nosaj.io/patron-page-timelapse.gif" alt="" />
</div>

This is the most technical part of this guide, and it isn't all that technical, which is a good thing.

There's an example of the page that I made here, and I've dumped the code in [a git repo](https://github.com/nosajio/my-patron) too.

I won't go in depth about every part of the page. Instead I'll focus on the important stuff, like how to embed and customise the PayPal buttons, and where to put messaging aimed at potential supporters.

### Making better subscribe buttons
So you might have noticed that PayPal's button tool gives you hideous buttons to work with, but thankfully PayPal also give you the option to use your own button image. To add your own button image, change the `<input type="image" src="..." >` tag's `src` attribute to contain the url of your button image.

In the example I've changed the default image to something a little nicer.

### Messaging
Patreon has a way of making supporters feel close to creators because of the informal wall-like feature that they call "Posts". As a cheap way to replace this, I've put a section at the top of the page that can be used to either show a message to potential supporters, or even a video similar to YouTube's channel page.

## 3: Use MailChimp as a communication channel
One big feature that Patreon offers is the ability to communicate directly with supporters. This can be replicated easily by using MailChimp to collect email addresses of supporters. Once the supporters' addresses are in MailChimp, emails could be sent directly to supporters.

To make this possible, PayPal has a system called `Instant Payment Notification` (IPN) that basically works like a webhook that sends a notification to an outside URL every time a sale is made. There's [a excellent guide](http://kb.mailchimp.com/integrations/e-commerce/use-paypal-with-mailchimp) over on MailChimp's knowledge base that I used to get this to work. I recommend reading that guide for more information on connecting PayPal and MailChimp.

## There is Hope Beyond Patreon
Replacing Patreon with a custom page is so easy that if I had stakes in Patreon right now, I'd be concerned. I think that Patreon offers a useful service that makes it simple for creators to receive support from fans without worrying about running a support platform. But what if running a support platform could actually be easier and cheaper than using Patreon in the long term? There is a lot of potential in this—and if Patreon continue to rock the boat, we will no doubt see more people jump ship, and self-hosted solutions like this will become more common.
