---
title: 'Data First Design'
synopsis: 'How a "data-first" approach to design can inform the structure of our user interfaces.'
xpost: 'https://metabroadcast.com/blog/data-first-design'
---

In this post I'm going to explore how a data first approach to design can be used to create simple and functional UIs.

### content first

Content first is a strategy developed for creating web pages, but with some small changes it can be optimised for making data-driven applications. The difference between content and data is that content usually comes to us as independent blocks of information. Data on the other hand has structure, and can be relational.

Human beings are inherently information driven, so it makes sense that we think about data before anything visual enters the mind. We think about what we need to tell the computer and what it needs to tell us, then we think about turning that information into something usable.

Thinking about the data model before anything else will reveal things about the interface that you probably hadn't thought of. Let me demonstrate this to you with a contrived example...

### the process

I'm really bad when it comes to starting to watch new TV shows, so I want to make a way for my friends to recommend shows for me. First of all let's think purely in terms of data: what does the app need to communicate in order to do its job? It should probably tell us the title of the show, maybe a cover image, who recommended it, and a link to the video might be nice. What about interactions? Well, it might be cool to score the recommendations and let my friends know whether I like the show or not.

Now we've decided on those things, let's think about how we should structure that data for this little app – I'm using JSON because it forces you to make decisions about hierarchy:

```json
[{
    "title": "Breaking Bad",
    "video_cover": "http://...",
    "video_link": "http://...",
    "recommendation": {
        "recommended_by": "Matt",
        "my_score": "4"
    }
},
{
    "title": "Archer",
    "video_cover": "http://...",
    "video_link": "http://...",
    "recommendation": {
        "recommended_by": "James",
        "my_score": "5"
    }
},
{
    "title": "Cosmos",
    "video_cover": "http://...",
    "video_link": "http://...",
    "recommendation": {
        "recommended_by": "Abi",
        "my_score": "4"
    }
}]
```

Just from looking at the data model, we start to see the interface revealing itself to us. It's clear that the cover and title will be important components. Pressing on the item will most likely link to the video, and we'll probably need a mechanism for scoring the show. These questions have all been posed and answered before thinking about form. Speaking of which, now's a good time to think about what this thing should look like.

![Data first](https://c4.staticflickr.com/4/3930/15233660009_0347da4548_b.jpg)

You can see the evolution. Patterns that the data model exposed are visible in the interface. Some wording has been added here and there to make the experience more natural, but the data structure is playing a big part in tying everything together. The next logical step will be to build a working prototype using the real data from before.

### wrapping up

The web is becoming increasingly service based (I'm certain that in the next few years your washing machine will have an API) and that's great because it means makers have access to tonnes of data that can be used to make all manner of useful things.

So there we are, using a data first approach to solve design problems. I hope you enjoyed this one :)
