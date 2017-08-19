---
title: I Made an App For Making Podcasts From YouTube Videos
category: "writeup"
coverImg: "http://a.nosaj.io/cover--ripcast.jpg"
coverColor: "#8CFFBA"
---

This is about a universal web application that I just got done with making called [Ripcast](http://ripcast.in). Ripcast solves a real problem for people who enjoy listening to YouTube content, and up to now, have had to wrestle with the YouTube app to make it possible.

## The Problem
Late one evening in April 2017, I was reflecting on how frustrating the YouTube experience makes listening to audio-only content.

That wasn't the first time YouTube's user experience had annoyed me. This is probably because I'm not the average YouTube consumer; my YouTube "Watch later" playlist is filled with content like lectures, talks, interviews, and other radio-type shows that I want to *listen to* and not watch. I usually like to listen to this sort of content while doing other things. If you've ever tried to use the YouTube app to consume content in this way (especially if you're carrying your device in your pocket), this frustration will be all too familiar.

### Less Than Ideal YouTube App Behaviour
The YouTube app will do things that makes passive use almost impossible:

- App will sense taps while the device is pocketed, causing play / pause to be activated, and sometimes a related video will magically start to play.
- When the video is pocket-skipped, the YouTube app sometimes forgets playback position after navigating back to original video.
- No sleep function.
- No save offline (this is more problematic when using on cellular, as long videos can weigh hundreds of MB to GB).

<div class="emphasis">
	<p>They say you should write software that will scratch your own itch. So that's what I did. I came up with a better way to listen to the YouTube content I love: turn it into podcasts.</p>
</div>

## The Solution
<div class="video">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/zZepgtPbdEI?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>
</div>

The premise of Ripcast is simple: it's a tool for creating and sharing podcasts made from YouTube content. For example, here is the feed for the podcast I made in the demo video above containing startup talks. 

<p class="center">http://app.ripcast.in/feeds/59970d59497ac629eb0ae1fc.xml</p>

You can paste that URL into your favourite podcasts app just like you normally would. When I add new content to that podcast using Ripcast, you will automatically see it show up in your podcast app!

For Ripcast to be worthwhile, I knew from the start that it had to be two things:

1. **⏱ Convenient**: I should be able to open up the app before commuting or going for a run and add a bunch of content. After this, my podcast app should automatically see the new content without any effort from me.

2. **⚡️ Fast**: adding and removing content should not require more than one or two interactions after opening the app. After pressing 'Add', I'd expect that content to be ready for listening almost immediately.

By writing down these two goals early, they helped to define what I should focus on while making Ripcast. Notice that the goals aren't concerned with implementation details, but about *how* the product will work.

## Controversy
Now, I should address this. I knew going in that this idea would be controversial, given that there is a lot of copyright restricted content and music on YouTube, and Ripcast ignores all of the guidelines right now. Google's terms of service make it clear that accessing YouTube content through means other than 'streaming' through YouTube is not permitted<sup>1</sup>.

To deter users from using Ripcast for copyrighted music, I made the file processor save audio at a resolution that is low enough for music to sound awful (64kbps) but works just fine for spoken content.

I still blazed on with development because I didn't see any ethical problems with doing so. The only loss to creators is ad revenue, but people still prefer to watch YouTube content when they can. I'll be surprised if this little app gains such reach to even scratch the surface of YouTube ad revenue.

## The Prototype
<div class="image">
  <img src="http://a.nosaj.io/ripcast/ripcast-proto.png" alt="Ripcast prototype: adding content" />
  <div class="caption">The prototype was a command line thing I hacked together in an evening.</div>
</div>

Making software shares more with other art forms than most people realise. Take writing an essay or painting a portrait for example. Upon starting to write or paint, it's difficult to envision the exact path one should take from the beginning to the end. 

In software, to solve this, we usually make prototypes. A prototype is kind of like a sketch: it's a quick and dirty implementation that should meet some of the main goals, but not necessarily all of them. Also like a sketch, parts of the prototype may be kept as a guide for later work.

The prototype for Ripcast was made in an evening, and was nothing more than a bunch of third party libraries that I plumbed together and ran on my MacBook. The prototype I made worked entirely on the command line. I could give it a YouTube URL and it would proceed to download the video, convert it, and then save an .mp3 to disk. 

From the prototype, I wanted to learn how viable the downloading and storing of YouTube content for multiple users would be. The questions I wanted to answer were (with answers for convenience):

- How long will it take to download and convert a single video? **about 2-3s per minute of video on my MacBook, but about 1s/minute with Linode's 40Gbps download**.

- How small can I get the final output file to be? **Using FFMPEG, I was able to squash files to about ½MB per minute of audio. Plenty small enough for storing cheaply**.

- Could the app run on the [cheapest single core Linode instance](https://www.linode.com/pricing) money can buy? **Linode instances use [Intel E5](https://www.intel.com/content/www/us/en/products/processors/xeon/e5-processors.html) chips which run at around ~2.2Ghz per core. This was a lot slower than my MacBook Pro, but I figured Linode's furious bandwidth would level things out (it made the process even faster)**.

It's worth saying that coding isn't required for making a prototype. Pieter Levels once [wrote about this](https://levels.io/product-hunt-hacker-news-number-one/) after he made a "crowdsourced spreadsheet as an MVP":

> Instead of building a site first, I simply a made public Google spreadsheet to collect the first data and see if there’d be interest for this at all[...] It quickly filled up and with Twitter going crazy about just a spreadsheet list, I had just answered the hypothesis if there’d be interest for this. There was some proprietary data people put on there which I deleted (like Numbeo) and made sure it was all crowd sourced public (and open) data.

**Don't assume you have to have a special set of skills to make good software. Making software is about improvisation and pragmatism as much as it is about coding.**

## Designing The UI
The two guiding principles I set for this project involved focussing on convenience and speed. I knew that failing to meet these two criteria would result in an objectively bad user experience.
 
<div class="box">
	<h3>Planning The UI</h3>
	<div class="image">
		<img src="http://a.nosaj.io/ripcast/ripcast-planning-ui.png" alt="" />	
	</div>
	<p>Instead of wasting time labouring over pixel perfect mockups, I opened a double spread in a notebook and designed the UI with a pen. Not only is designing like this more freeing, it's also more effective for idea generation. You want to work with a medium that allows you to try new ideas very quickly. Who cares if it looks messy at this point. All ideas come out messy at first anyway, what you do with them next is more important.</p>
</div>

### Designing for speed
There is an inevitable learning curve for every new piece of software we use. One job of the designer is to keep that learning curve as smooth as possible. When a user has to stop and think – or "trips" – the designer has failed. If we visualise the ideal learning curve, it would look like a smooth concave that rises quickly, while a bad curve will look more convex.

<div class="image">
	<img src="http://a.nosaj.io/ripcast/ripcast-learning-curves.png" alt="" />
</div>

Smooth learning curves are hard to achieve because every user experience is uniquely subjective. The best we can do when designing software is to fall back on likely familiar patterns wherever possible. When the user is already familiar with some of the software, the amount of cognitive effort required for understanding it will be less. As a result, the thing will be easier to learn because the new elements are buttressed with familiar ones. This is why copying what everyone else does can be good for users.

## Making The File Processor
In order to efficiently turn YouTube videos into audio files, I had to white some code that could handle the downloading and conversion of YouTube content. This part of the application is aptly called the file processor.

The file processor runs separately from the main app server. By dividing them up, it's possible to have multiple instances of the file processor running as workers, and of course, multiple workers means concurrent processing. This prevents users from blocking one another when adding content at the same time.

<div class="image">
	<img src="http://a.nosaj.io/ripcast/ripcast-content-pipeline.png" alt="" />
	<div class="caption">The app server and processor run as separate processes</div>
</div>

To pass data between the app server and the worker process(es) I used a [Redis](https://redis.io/) server as a queue. This works a lot like an assembly line: the app can push data into the queue as it pleases, and a worker will only ask for the next item when one becomes available.

I tuned FFMPEG and the file processor until it was able to process a minute of YouTube content in around a second. If I add 1 hour of content to Ripcast, it will be available for me to start listening to in about 60 seconds.

## What's Next for Ripcast?
Well, if I don't get my door kicked in by Google, I hope that people will find value in having more flexibility around consuming the content they enjoy. 

There are lot's of creators who receive support from their audience through Patreon [or other means](https://www.nosaj.io/r/replace-patreon) (especially since the ad-pocalypse). Ripcast, I think, will help these creators more than hinder them because it gives audiences more flexibility in how they choose to consume content.

For the creators reliant on YouTube ad revenue, I think they will be less receptive to Ripcast, and I understand that. But I don't expect Ripcast will ever see enough users to make a dent in ad revenue for these creators anyway.

## Ideas & Suggestions
If you have any thoughts about Ripcast, please [tweet me](https://twitter.com/__nosaj) or email me on hi (at) nosaj (dot) io.


<sup>1</sup>: Still, this doesn't stop people from downloading mp3's (with [tools](http://convert2mp3.net/en/) [like](http://www.youtube-mp3.org/) [these](http://www.flvto.biz/)) for their own personal use. Ripcast is a free service that automates this process further by generating a podcast feed for the converted content. As there are already a whole load of sites that let you download YouTube content, I figured I'd just go ahead with the project and see what happens.
