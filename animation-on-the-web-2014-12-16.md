---
title: 'Animation and the Web'
synopsis: 'Thoughts on the future of the web animation api'
xpost: 'https://metabroadcast.com/blog/animation-and-the-web'
---

Moore's Law tells us that the size of computer chips gets exponentially smaller while at the same time getting exponentially cheaper over time. This concept of accelerating change can be applied to technology as a whole. With this being the case, how can we — the people working inside the technology industry — have any chance of keeping up to date with the constant changes to our toolkit?

For me at least, it's becoming close to impossible to keep up with the race without spending most of the day reading about it all, so I've adopted a new strategy: only pursue what sounds the most exciting. The other stuff can wait.

### hello web animation api

One of the things that I'm very excited about at the moment is the Web Animation API, and what it will mean for the ways we interpret, and interact with, the web. There's a [lot](http://updates.html5rocks.com/2014/05/Web-Animations---element-animate-is-now-in-Chrome-36) [of](https://www.youtube.com/watch?v=ep0_0W0qWsc) <a></a> [content](http://web-animations.github.io/web-animations-demos) out there about how the API works, so instead in this article I'm going to talk about what this technology will enable us to do in the future, and how it will be good for the users of the things we make.

If you've never heard of the Web Animation API, I encourage you to read [this excellent article](http://www.smashingmagazine.com/2014/11/18/the-state-of-animation-2014) over on Smashing Magazine. It's quite a long one, but it explains the overall philosophy behind the API, as well as example use cases.

Designers who use the current methodology for creating and controlling web animations have been bound by the cumbersomeness of using CSS keyframe animations combined with Javascript, which feels like a hack approach. The Web Animation API will make this approach obsolete. It already outperforms CSS keyframe animation, it has support for motion paths, post-animation callbacks, it integrates with SVG, and it feels… natural.

### looking ahead

Looking into the future of this technology is where things get really interesting. Think about the movement we've seen in the native app marketplace with UI animations. What some people don't realise is that animations aren't just an aesthetic component, but a UX component also. They can help provide context and a state of position inside an application. They can also be used to make things _feel_ amazing to use.

Now imagine what will happen when this level of animation control meets the web. Like anything that meets the web, it will explode. We will see all of the great animation UI concepts from native applications applied to the web, and the nature of the web being a more adaptive and transient medium than native apps will surely create an environment for great leaps in innovation. I personally am looking forward to the times ahead.

### how can I use this now?

The Web Animation API is a W3C specification, meaning it's a standardised spec across all browsers. [You can read it here](http://w3c.github.io/web-animations/). At the moment you can only use the Web Animation API in Chrome and Firefox nightly builds, and it will be coming to a browser near you soon. In the meantime though, if you want to get stuck in early [check out the shim over on GitHub.](https://github.com/web-animations/web-animations-js)
