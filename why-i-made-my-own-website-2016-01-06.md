---
title: 'Why I Made My Own Website in 2016'
synopsis: 'Despite the range of products for writing and hosting content online, I decided to go from scratch.'
---
Once upon a time, the world wide web was more like the wild west than Time Square. This was a time when only the brave ventured out into this world of unknowns to explore the boundaries of HTML and HTTP, and maybe build a little place of their own online.

This short phase that later acquired the moniker "Web 1.0" might one day be remembered as nothing more than a blip in time. The short calm before the masses gravitated to the web when – to most people – it was still a gimmick.

This was a time before the internet was a place that contains all the websites we go to; before Facebook, MySpace, Twitter and Instagram opened their doors. If you wanted to put something on the web back then you would have to learn how to write markup, how to host a website (probably with your ISP), and eventually learn how to express yourself on screen with tables and text. 

***

Nowadays when you want to host content online, you're suddenly slapped with a list of decisions before you can even think about content. The list usually starts with: which platform or service should I use? Do I want to self host or use a hosted service? What are the pros and cons?… and so on.

I've watched as many of my friends who are starting their own respective project's online get greeted with this rather large hurdle. A hurdle that get's higher as time passes and more names get added to the list of platforms and services.

Before starting work on this website in early December I was in a similar position. I explored a lot of options before going forward, some just out of curiosity and others because I was genuinely interested in using a third party tool for my writings. Here's the outcome of my research into writing platforms:

### The Hosted Options
Hosted options like Medium, Wordpress hosted, Blogger etc were originally where I looked. To me these products are great for writing short disposable pieces, but they're not where I want to host my creative work. 

It's not a new thing to be wary of The Cloud™ as a long term safe storage mechanism<sup>1</sup>. Services come and go all the time and people loose their data, yet we still keep on putting all our eggs in the most convenient basket.

### The Self-hosted Flatpack Options

These are things like Wordpress and Ghost who offer a flatpack host-it-yourself downloads and give you a decent set of tools for hosting a website or personal blog. This is good, but from experience it can require some hacking if you want anything outside of default functions. That and the inevitable [feature debt](https://en.wikipedia.org/wiki/Technical_debt). 

There's also the "static blog" options, like Jekyll. I've used [Jekyll](https://jekyllrb.com/) in the past for numerous blogs and projects, but for this project I was more interested in using Javascript, and unfortunately Jekyll is written in Ruby.

None of the options hitherto excited me very much.

### The Roll-up-your-sleeves Option

This option was to do it all myself. This excited me the most because it was an opportunity to make something fun and new, but it also made me think of the old days; the wild west days of the web.

It feels rather against the grain to make your own self-hosted, self-designed _and_ self-built website or blog nowadays, but its easier than ever with the tools available. Well, if you don't mind writing some code and know your way around NGINX and have an AWS account it is, but these things are easy enough to learn if you just dive in and make stuff.

I'll be writing a technical follow up post to this one soon that goes more in depth on how exactly I went about building and hosting this website for those of you who are into that… you know who you are.

***

After some thought I had come to the decision that whatever I made should be super simple in design and execution. I wanted to play to the strengths of making my own website, and not build another monolith. 

I decided to concentrate on:

**Speed**: it should be fast all of the time, whether you're on a 1GBps fibre or a GPRS connection.

_I wanted to make the fastest blog that I've ever used._

**Cheapness**: that's right, I'm a cheapskate. But really, hosting your own stuff always comes at a price, and I should make an effort to design something that is low cost to run.

**Creative freedom**: I had a blank canvas to do with anything that I desired, so I wanted to use the opportunity as a way to exercise my web muscles.

## Designing it: Hosting Content
Before starting I thought a lot about the most appropriate way host my writings. The ideal solution should allow my posts to be saved as flat [Markdown](https://daringfireball.net/projects/markdown/) files, and it should allow the data to be accessible to the blog, be safe from accidental deletion, and be easy to update when I publish new content. 

You can never be too careful when it comes to backing up your stuff — there's a saying "Two is one and one is none" that says it all.

After some thought, I landed on GitHub for hosting my posts. Sure it's still in The Cloud™, so not entirely in my control, but GitHub are notoriously trusted for keeping data safe. GitHub also has history support, and all the wondrous features of git. As a precaution, I will still keep a backup on my local machine, and one on a backup drive.

Not many people realise that GitHub has webhook support<sup>2</sup>, so when a push is made to the repository it will automatically send a HTTP request to a URL of your choice. This was to be the mechanism I'd use to alert my service that a change has been made to the data. The service could then do a pull on the git repository which contains my blog posts and update its data to the fresh version. You can see [my "writing" repo](https://github.com/jasonhowmans/writing) for yourself.

### Designing it: The Posts Service
Above I alluded to the service that I'd have to make to expose the post data as structured [JSON](http://www.json.org). The service needed to exist to translate the Markdown files on GitHub into something readable by the front end.

The service would need to have a series of simple jobs. It should pull the Markdown files from where they're hosted on GitHub, covert the Markdown to HTML, perform some fancy date operations, add some bells and whistles, and expose it all as an API. Most importantly, it should do everything very very quickly.

I'll cover the technicalities of service in my follow up post.

### Designing it: The Front End
Between the two desirables that I'd decided on — speed and creative freedom — the front end already had a lot to live up to. 

I read a lot of blogs that have great content but suffer with terrible usability. The typography is usually what suffers the most, but speed and lack of mobile support are also common experience killers. I didn't want my blog to suffer in any of these areas so I made sure every decision would be looked at through the filter of speed and good usability.

If the service is online and completing requests at ~10ms (minus download times) then much is already in place to make a lightening fast blog. All that will be left to do is make sure the front end runs efficiently; not downloading the full page and all assets for every page change, and making sure the first page download is small are a couple of things that go a long way to make a snappy front end. Another good exercise in efficiency is to remove any assets that aren't absolutely necessary.

Legibility is a difficult thing to design well because it requires dedicated time and testing to get right. From the start I worked with a legible serif font (Droid Serif) for long form text, as serif fonts have a bit more weight they can be easier on the eye for long form text. I then chose a sans serif typeface (Soleil) to be used for headings and short form content.

I tuned fonts to a range of comfortable sizes based on a modular scale of 1.414 that adapts based on the size of the screen, and the same for line height, line length, and spacing between elements.

But this is the web after all, so the experimentation is not over. I intend to tune the design iteratively as time goes on based on feedback, and to allow the project to evolve on its own.

***

This post has ended up being way longer than I'd originally planned, so if you're still with me at this point I'm very grateful for your attention! 

I'll be posting over here up to couple of times a week from now on. I plan to write mostly about web technology, how to make the web a better place to work and play, subjects like human behaviour, and anything I think may be helpful or interesting to write about.

***

1. [Fuck The Cloud (2009)](http://ascii.textfiles.com/archives/1717)
2. [GitHub Webhooks](https://developer.github.com/webhooks/)
