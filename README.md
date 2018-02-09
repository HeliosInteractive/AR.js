# AR.js - Efficient Augmented Reality for the Web

This project provides all the tools needed to easily test and implement multiple types of web based AR/VR projects. 

Be advised that content is changing rapidly.

- **Very Fast** : Runs efficiently on most devices. See Performance data. (https://twitter.com/jerome_etienne/status/831333879810236421)!
- **Web-based Standards** : Works with **any browser with WebGL and WebRTC** no installation or app required.
- **Multi-platform** : Android, IOS (Must be IOS 11), Windows phone, Windows, OSX
- **Open Source** : It is completely open source and free of charge!

[![AR.js 1.0 Video](https://cloud.githubusercontent.com/assets/252962/23441016/ab6900ce-fe17-11e6-971b-24614fb8ac0e.png)](https://youtu.be/0MtvjFg7tik)

If you wanna chat, check [![Gitter chat](https://badges.gitter.im/AR-js/Lobby.png)](https://gitter.im/AR-js/Lobby)


# Marker Based AR/VR

While AR.js is experimenting with other tracking methods, the core feature AR.js offers is marker-based tracking, made possible via an asm.js port of ARToolKit5.

Learn more about marker types, limitations, and marker training at [ARToolKit's documentation site](https://www.artoolkit.org/documentation/).

# Project Status

- Three.js implementation is working efficiently. [three.js examples in source](https://github.com/jeromeetienne/AR.js/tree/master/three.js/examples)

- aframe exporting ```<a-marker>``` tags will make it easier to use. - See Info here: [aframe-artoolkit](http://jeromeetienne.github.io/slides/artoolkit-aframe/) [aframe examples in source](https://github.com/jeromeetienne/AR.js/tree/master/aframe/examples)

- Babylon.js implementation is working as well. [babylon.js examples in source](https://github.com/jeromeetienne/AR.js/tree/master/babylon.js/examples)

- webvr-polyfill: Work-in-progress. [webvr-polyfill examples in source](https://github.com/jeromeetienne/AR.js/tree/master/webvr-polyfill/examples)


# Try out AR in your browser now with your desktop and mobile device!

1. Open this [HIRO marker image](https://jeromeetienne.github.io/AR.js/data/images/HIRO.jpg) in your desktop browser.

2. Open this link [Augmented Reality Viewer - Example](https://jeromeetienne.github.io/AR.js/three.js/examples/mobile-performance.html) in your phone browser, and point it to your screen.

**Ready to go?!** Use your mobile device to view the HIRO marker image on your mobile device to reveal the example Augmented Reality.

![screenshot](https://cloud.githubusercontent.com/assets/252962/23072106/73a0656c-f528-11e6-9fcd-3c900d1d47d3.jpg)

# Project Tools and Examples

- Pattern Marker Training: [Pattern Marker Training](https://archive.artoolkit.org/documentation/doku.php?id=3_Marker_Training:marker_training)
- Generate a pattern marker with your own image. [Barcode](https://archive.artoolkit.org/documentation/doku.php?id=3_Marker_Training:marker_barcode) and [Multi](https://archive.artoolkit.org/documentation/doku.php?id=3_Marker_Training:marker_multi)
- [ARCode Generator](https://jeromeetienne.github.io/AR.js/three.js/examples/arcode.html) :
  Generator of AR-Code ([source](https://github.com/jeromeetienne/AR.js/blob/master/three.js/examples/arcode.html))
- [WebAR Playground](https://webxr.io/webar-playground/) :
  Playground running in WebAR with ar.js/chromiumAR

[ALL EXAMPLES - MANY OLD LINKS](https://jeromeetienne.github.io/AR.js-docs/misc/EXAMPLES.html)

## A-Frame example

Detailed walkthrough at ["Augmented Reality in 10 Lines of HTML - AR.js with a-frame magic"](https://medium.com/arjs/augmented-reality-in-10-lines-of-html-4e193ea9fdbf)
by
[@AndraConnect](https://twitter.com/AndraConnect).

```html
<script src="https://aframe.io/releases/0.5.0/aframe.min.js"></script>
<script src="https://jeromeetienne.github.io/AR.js/aframe/build/aframe-ar.js"></script>
<body style='margin : 0px; overflow: hidden;'>
	<a-scene embedded artoolkit='sourceType: webcam;'>
		<a-box position='0 0 0.5' material='opacity: 0.5;'></a-box>
		<a-marker-camera preset='hiro'></a-marker-camera>
	</a-scene>
</body>
```

See the result on [codepen](https://codepen.io/jeromeetienne/pen/mRqqzb)

# Browser Support

Any browser that supports **WebGL** and **getUserMedia/Stream API** can run AR.js.

See caniuse.com for up-to-date browser support metrics: [WebGL](https://caniuse.com/#feat=webgl), [getUserMedia](https://caniuse.com/#feat=stream)

### Desktop Browsers
- Chrome
- Firefox

### Mobile Browsers
- Chrome on Android
- Safari on iOS 11

### Common Causes for Failure
If the browser you are using _should_ be able to run AR.js, but doesn't, there are several potential causes.
#### Unable to access camera via `getUserMedia`
- The webpage is served through `http` instead of `https`, which doesn't allow user media access.
- The webpage is opened inside another app through a webview, which doesn't support `getUserMedia`.
  - In this situation, try opening the same url in mobile Chrome/Safari.
- The webpage couldn't detect the device's camera.
- The device does not have a camera.
#### Unable to create WebGL context
- The browser doesn't support WebGL.
- WebGL is blocked for the device's graphics driver version.

# Performance

There are three determining factors for performance:

1. How large is your 3D/AR?
2. How you tune your parameters? **More info soon**
3. Hardware!

We hope to have additional benchmarking results soon.

- 60fps stable on Nexus 6P
- 50+fps on Nexus 5X [~50fps on a old nexus5, and ~60fps on nexus 9](https://twitter.com/Ellyll/status/834312442926751744)
- [Sony Xperia Z2 (2.5 years old) runs around 50fps](https://twitter.com/leinadkalpot/status/834121238087925763) - This is a 170 Euro phone.
- Some reports [~50fps on a old nexus5, and ~60fps on nexus 9](https://twitter.com/Ellyll/status/834312442926751744) 
- [40-45fps on lumia 930](https://twitter.com/fastclemmy/status/834817155665391616) for others.


# Researches, Resources, and Recommended Readings

## Experimentation

Recently, we’ve been getting creative and working on developing new things with AR.js. One of them is playing around with [shadows](https://twitter.com/jerome_etienne/status/837240034847764480), syncing the position of virtual lights with reality for a more life-like finish:
![screen shot 2017-03-16 at 21 06 24](https://cloud.githubusercontent.com/assets/6317076/24018623/7f787ba8-0a8c-11e7-8088-fea4799b5d09.png)

We’ve been collaborating very closely with [Fredrick Blomqvist](https://twitter.com/snigelpaogat). His input has had a great impact on AR.js innovation and we want to thank him. Together, we’ve been implementing [refraction](https://twitter.com/jerome_etienne/status/838749280999518208), giving the 3d a transparent/glassy effect. It ended up having a nice polished look.
![screen shot 2017-03-06 at 16 31 28](https://cloud.githubusercontent.com/assets/6317076/23832948/9b64c79e-0736-11e7-9cb8-747f6a8fc082.png)

Other crazy ideas we’ve been working on include a [hole in the wall](https://twitter.com/jerome_etienne/status/836754117964017664) and a [portal into another world](https://twitter.com/jerome_etienne/status/838404908235776000). We want to take AR.js to new dimensions.
![screen shot 2017-03-12 at 15 19 51](https://cloud.githubusercontent.com/assets/6317076/23833024/b2e045be-0737-11e7-9ef0-8e1ac9e49ba8.png)
![screen shot 2017-03-07 at 10 08 39](https://cloud.githubusercontent.com/assets/6317076/23833015/947f6abe-0737-11e7-9a0d-1ea919f6ffbe.png)

## Augmented Website
[Seminal post](https://medium.com/arjs/augmenting-the-web-page-e893f2d199b8) explaining the concept.
The service is available [webxr.io/augmented-website](https://webxr.io/augmented-website/)

[![Augmented Website](https://user-images.githubusercontent.com/252962/27472386-0d11e59a-57f3-11e7-9fa5-34332c5484f7.png)](https://webxr.io/augmented-website/)

## AR.js blog

The project started a [AR.js blog](https://medium.com/arjs) to keep everyone up to date. Please check there for the newest content.

## Additional Recommended Reading

- How to write a AR.js application?
Here is a [full tutorial](https://marmelab.com/blog/2017/06/19/augmented-reality-html5.html)
by [marmelab](https://marmelab.com/) featuring [François Zaninotto](https://twitter.com/francoisz).
It explain how to code a full application on phone! Step by Steps, with explaination and videos. 
Very great! the perfect step if you want to start writing AR application today.
- Great post about [WebAR for designer](http://www.nexusinteractivearts.com/webar/)
by [nexus interactive arts](http://www.nexusinteractivearts.com/)
-This is highly creative! Just look at this [puzzle game in #AR playing with mirror and laser beam](https://www.youtube.com/watch?v=OzLJb7HitvA).
- Augmented reality on phone have applications in many fields: [history education](https://www.youtube.com/watch?v=gyp8ZYtyu_M) , [science](https://www.youtube.com/watch?v=gMxdBdLpVgc) and [gaming](https://www.youtube.com/watch?v=kEMDgvfFUcI).

# Standing on the Shoulders of Giants - Acknowledgements

It is now possible to do 60fps web-based augmented reality on a phone.
This is great for sure but how did we get here ? **By standing on the shoulders of giants!**
It is thanks to the hard work from others, that we can today reach this mythic 60fps AR.

Please thank and contribute to these teams:

- **three.js** for being a great library to do 3d on the web.
- **artoolkit**! years of development and experiences on doing augmented reality
- **emscripten and asm.js**! thus we could compile artoolkit c into javascript
- **chromium**! thanks for being so fast!



> "Only thanks to all of them, I could do my part : Optimizing performance from 5fps on high-end
phone, to 60fps on 2years old phone. After all this work done by a lot of people, we have a *web-based augmented reality solution fast enough for mobile*! Now, many people got a phone powerful enough to do web AR in their pocket. I think this performance improvement makes web AR a reality and I am all exited by what people are going to do with it :)" - Jerome Etienne

"Shared #ar is a lot more real than solo #AR." - Augmented reality principle [tweet](https://twitter.com/jerome_etienne/status/847889867296124933)

"The marker must be a portal from where the virtual emerges." by @AndraConnect - #AR principles at dinner 😏 [tweet](https://twitter.com/jerome_etienne/status/842112692211056640)

# Licenses
jsartoolkit5 is under LGPLv3 license and additional permission.
Other code in AR.js repository is under MIT license.

For legal details, be sure to check [jsartoolkit5 license](https://github.com/artoolkit/jsartoolkit5/blob/master/LICENSE.txt)
and [AR.js license](https://github.com/jeromeetienne/AR.js/blob/master/LICENSE.txt).

# Change Log
[CHANGELOG.md](https://github.com/jeromeetienne/AR.js/blob/master/CHANGELOG.md)

# What's Next ?

We did good on performance, but there are still a lot of room for optimisation.
Using [webworkers](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Using_web_workers)
would increase cpu usage. Compiling in [webassembly](https://webassembly.org) instead
of [asm.js](http://asmjs.org/) should improve loading time and likely cpu performance.
And obviously, we can still do more parameters tweaking :)

### Future

[FUTURE.md](https://jeromeetienne.github.io/AR.js-docs/misc/FUTURE.html)

# FAQ

[FAQ.md](https://jeromeetienne.github.io/AR.js-docs/misc/FAQ.html)

# How To Release ?

```bash
# replace REVISION to the proper version
atom three.js/src/threex/threex-artoolkitcontext.js package.json README.md

# Rebuild a-frame and webvr-polyfill
make minify

# Commit everything
git add . && git commit -a -m 'Last commit before release'

# Go to master branch
git checkout master

# Merge dev branch into master branch
git merge dev

# tag the release
git tag 1.5.1

# push the tag on github
git push origin --tags

# push commits tag on github
git push

# update npm package.json
npm publish

# Come back to dev branch
git checkout dev

# update the a-frame codepen
open "https://codepen.io/jeromeetienne/pen/mRqqzb?editors=1000#0"
```