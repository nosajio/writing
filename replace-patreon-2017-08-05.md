# Replacing Patreon With PayPal and MailChimp

About a week ago, Journalist Tim pool sent out a tweet asking if anybody could help him create a simple subscriber platform for donors. 

[https://twitter.com/Timcast/status/890704719840030726]

This came after Patreon shut down the account of a journalist without any warning, causing content creators to wonder if their name could be on the ban list, too.

After looking into the work involved in hacking together a Patreon-like system, it became apparent that that Patreon might be easier and cheaper to replace than I had first anticipated. In the following rough guide I will show you how to make and host your own subscriber platform that will be resistant to the whims of Silicon Valley.

## Prerequisites 
Before we get started you'll need a PayPal Business account to make this possible. It also helps if you understand enough about HTML to make a simple webpage.

#### Why PayPal
When I started writing this, I was set on the idea of using Stripe to handle subscriptions and billing, as they have some nice ways of keeping everything in one place. But I realised that it wasn't the best approach as the Stripe solution started to get more complicated. The idea of this project is to see if I can easily replace Patreon's core features with web services, and PayPal offer a simple solution with their hosted button system.

#### Cost
PayPal don't make it clear how much they charge for using hosted buttons, but I'll assume that they will take their usual percentage of 2.9% from each transaction. Patreon's transaction fee is 5%, so this method will give 2.1% back to creators per transaction.

## STEP 1: Setup PayPal Subscription Tiers
[img]

To receive payments, we'll need to tell PayPal what to charge people when they press on the "Subscribe" button. To do this, [PayPal have a form](https://www.paypal.com/buttons/select) that you can use to setup prices and customise how your button looks.

[img]

Now that your button has been described, PayPal will generate some code that will need to be pasted into the page that we'll make next.

## STEP 2: Making the Support Page
[img]

This is the most technical part of this guide, and it isn't all that technical, which is a good thing.

There's an example of the page that I made here, and I've dumped the code in [a git repo](https://github.com/nosajio/my-patron) too.

I won't go in depth about every part of the page. Instead I'll focus on the important stuff, like how to embed and customise the PayPal buttons, and where to put messaging aimed at potential supporters.

### Making better subscribe buttons
So you might have noticed that PayPal's button tool gives you hideous buttons to work with, but thankfully PayPal also give you the option to use your own button image. To add your own button image, change the `<input type="image" src="..." >` tag's `src` attribute to contain the url of your button image.

In the example I've changed the default image to something a little nicer.

### Messaging
Patreon has a way of making supporters feel close to creators because of the informal wall-like feature that they call "Posts". As a cheap way to replicate this, I've put a section at the top of the page that can be used to either show a message to potential supporters, or even a video similar to YouTube's channel page.

## STEP 3: Use MailChimp as a communication channel
One big feature that Patreon offers is the ability to communicate directly with supporters. This can be replicated easily by using MailChimp to collect email addresses of supporters. Once the supporters' addresses are in MailChimp, emails could be sent directly to supporters.

To make this possible, PayPal has a system called `Instant Payment Notification` (IPN) that basically works like a webhook that sends a notification to an outside URL every time a sale is made. There's [a excellent guide](http://kb.mailchimp.com/integrations/e-commerce/use-paypal-with-mailchimp) over on MailChimp's knowledge base that I used to get this to work. I recommend reading that guide for more information on connecting PayPal and MailChimp.

## There is Hope Beyond Patreon
Replacing Patreon with a custom page is so easy that if I had stakes in Patreon right now, I'd be concerned. I think that Patreon offers a indispensable service that makes it simple for creators to receive support from fans without worrying about running a support platform. But what if running a support platform could actually be easier and cheaper than using Patreon in the long term? There is a lot of potential in this—and if Patreon continue to rock the boat, we will no doubt see more people jump ship.