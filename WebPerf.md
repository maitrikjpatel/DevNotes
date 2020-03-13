---
date: '2020-3-12'
publish: 'true'
category: 'note'
author: 'Maitrik Patel'

title: 'Web Performance'
description: 'Most users rate webpage/application speed as being at the very top of the UX hierarchy.'

topics: 'tools, development'

source: 'Github'
---

## Articles

- [W3C Web Performance Working Group](https://github.com/w3c/web-performance/)
- [What is a browser engine?](https://hacks.mozilla.org/2017/05/quantum-up-close-what-is-a-browser-engine/)
- [Web Performance Made Eas](https://developers.google.com/web/updates/2018/08/web-performance-made-easy)
- [Why performance matters](https://developers.google.com/web/fundamentals/performance/why-performance-matters)

## Tools

- [PerfMap](https://github.com/zeman/perfmap)
- [Performance Bookmarklet](https://github.com/nurun/performance-bookmarklet)
- [How Web Works](https://github.com/vasanthk/how-web-works#googles-g-key-is-pressed)
- [Guess JS: Predictive Fetching](https://github.com/guess-js/guess)

## Topics

- [ResourceTiming](https://nicj.net/resourcetiming-in-practice/)
  - ResourceTiming exposes accurate performance metrics for all of the resources fetched on your page.
  - You can use this data for a variety of scenarios, from investigating the performance of your third-party libraries to taking specific actions when resources aren’t performing according to your performance goals.
- [Image Optimization Guide](https://images.guide/)
- [What is Preload, Prefetch, and Preconnect?](https://www.keycdn.com/blog/resource-hints)


## Web Performance Experts

- [Paul Irish](https://twitter.com/paul_irish?lang=en)
- [Harry Roberts](https://twitter.com/csswizardry)
- [Addy Osmani](https://twitter.com/addyosmani)
- [Mathias Bynens](https://twitter.com/mathias)
- [Steve Souders](https://twitter.com/Souders)
- [Suhail Doshi](https://twitter.com/suhail)

## Web Performance best practices

- **Minify** :
  - JS/CSS -> GZip

- **Caching** :
  - Efficient Caching policy to ensure that we don’t send resources twice if unnecessary.
  - Ideally you should aim at caching as many resources as securely possible for the longest possible period of time and provide validation tokens for efficient

- **Remove unused code** :
  - Use chrome code coverage tool to check unused code

- **Avoid enormous network payloads** :
  - Make an inventory of all assets
  - Measure value & impact of assets
  - Audit using `webpack analyzer` & `bundlephobia`

- **Lower JavaScript boot-up time with code splitting**
  - Why Js boot-up take time ?
    - Download JS -> parse -> compile -> execute
  - Code-splitting
    - split routes
    - split components
    - split vendor bundles
  - Tree shaking
  - Serve modern, small JS bundles

- **Optimize images**
  - Image optimization
    - Tool : imageOptim
    - npm Package : imagemin
  - Animation
    - FFmpeg tool to convert our animation GIF into the mp4 file.
  - Lazy-load off-screen images
    - Lazysizes library to only load image as per viewport

- **Help browser deliver critical resources early**
  - Hey, browser! Here’s a resource you’re going to need later on, so start loading it now.
  - Use link `preconnect`, or`preload` or `prefetch`
  - `<link rel="preload" href="late_discovered_thing.js" as="script">`
  - **preconnect**
    - Preconnect allows the browser to setup early connections before an HTTP request is actually sent to the server. 
    - This includes DNS lookups, TLS negotiations, TCP handshakes.
    - This in turn eliminates roundtrip latency and saves time for users.
  - **preload**:
    - Use for fonts, image, js, css
    - Preload key web fonts requests
    - The preload keyword is being added to the Link HTTP header and link HTML element.
    - This keyword provides a declarative fetch primitive that initiates an early fetch and separates fetching from resource execution.
    - The preload link element provides async-like semantics for non-script elements.
  - **prefetch**:
    - fetch resources, store them in cache for future use
  - **prerender**
    - Prerendering is very similar to prefetching in that it gathers resources that the user may navigate to next.
    - The difference is that prerendering actually renders the entire page in the background, all the assets of a document. 

- **Experimental: Priority Hints**
  - `<img src="/", importance="high">`
  - `fetch( 'url', {importance: 'low'})`

- **Reduce render-blocking scripts**
  - `cricical` : NPM module called Critical to inline our critical content in index.html
  - Inline first paint styles in our HTML, the browser is able to render them straight away without waiting for the external stylesheets to arrive.

- **Use Base64 wisely** : Check bottom for notes

- **On Webpage things to avoid**
  - Repaint
    - browser just repaints the element again with the new styles applied
  - Reflow
    - changes affect document contents or structure, or element position, a reflow (or relayout) happens
      - DOM manipulation (element addition, deletion, altering, or changing element order);
      - Contents changes, including text changes in form fields;
      - Calculation or altering of CSS properties;
      - Adding or removing style sheets;
      - Changing the "class" attribute;
      - Browser window manipulation (resizing, scrolling);
      - Pseudo-class activation (:hover).
  - Animate only absolute/fixed positioned elements if you can.
  - disable complicated :hover animations while scrolling (e.g. by adding an extra "no-hover" class to body)


## Case studies' notes

- [Pinterest PWA](https://medium.com/dev-channel/a-pinterest-progressive-web-app-performance-case-study-3bd6ed2e6154)
  - **Route-based JavaScript chunking** : 
    - Getting a web page to load and get interactive quickly benefits from only loading the code a user needs upfront.
    - Use **Webpack** to break out vendor bundles into their own cacheable chunk
      - https://webpack.js.org/plugins/split-chunks-plugin/
    - **Code Splitting**
      - https://github.com/ReactTraining/react-router/blob/master/packages/react-router-dom/docs/guides/code-splitting.md
    - **babel transpile** :Use babel-preset-env to only transpile what target browsers need
    - Use **Webpack Bundle Analyzer**
      - Move out common code from async chuncks into entryChunk
      - https://github.com/webpack-contrib/webpack-bundle-analyzer

  - **Image Optimization**
    - Pinterest also uses a progressive loading technique for images in their PWA.
    - React performance pain-points: Mounting and unmounting large trees of components (like Pins) can be slow
    - In the mean time, Virtualizing the grid helped significantly with component unmount time.
  
  - **Navigation Transitions**
    - Review Data before you can lod.
    - The user gets visual UI painted quickly while we’re waiting for the data to arrive.

  - **Redux**
    - https://github.com/paularmstrong/normalizr
      - normalizes nested JSON according to a schema
    - Pin IDs with the Pin component denormalizing itself. 
    - If there are changes to any given Pin, the full grid does not have to re-render.

  - **Caching assets with Service Workers**
    - Workbox
      - https://developers.google.com/web/tools/workbox
      - https://developers.google.com/web/fundamentals/instant-and-offline/offline-cookbook/ 

  - **V8**
    - V8’s code caching, helping skip some of the parse/compile cost on repeat views so they can load quicker.
    - Generating a Service Worker for each locale

  - **Application Shell challenges**

- [Pinterest Performance](https://www.youtube.com/watch?v=FBeR6QvroEQ)
  - Custom IMP metrics
    - PWT : Pinner wait time
    - Synthetic test
    - Regression test
  - Perf Watch
    - Merge to Master
      - create prod build
        - run tests
          - Perf Server 1 [Locked]
          - Perf Server 2 [Locked]
          - Perf Server 3 [Locked]
          - Perf Server 4
            - Docker server
              - 9 surface areas like
                - Search Page
                - Pin Close Up Page
                - Home feed Page
                - SEO Page
              - Each surface have threshold

  - Perf Detective
    - Each commit want to test
    - Run on Binary search of each commit
    - Give which commit introduced it
  - Regression Investigations
    - Ownership
    - Severity level, P2/200ms, P1/500ms, P0/1s
    - Investigation Run-book
  - Optimization strategy
    - AB Testing
    - Engagement impact
    - How much time it saves users
  - Education
    - Training
    - Consulting
    - Documentation
  - Resource timing
  - HTTP2

- [JS Faster](https://www.youtube.com/watch?v=RwSlubTBnew)
  - IE8 come with preloader
  - Paralyzation
  - 2009 - async
  - Make JS Faster
    - load scripts async
    - use prefer
    - use preload, `<Link role="preload" href="" as="script"> PreLoad <link/>`
    - reduce CPU time JS takes to load
    - Budget 3rd Party : third party JS vs 1st party JS
    - GZIP regression to first party scripts
    - Review Code coverage

- [Why not use Base 64 ?](https://csswizardry.com/2017/02/base64-encoding-and-performance/)
  - Base64 encoding increases filesize in ways that we can’t effectively mitigate (e.g. Gzip). 
    - This increase in filesize delays rendering, because it’s happening to a render-blocking resource.
  - Base64 encoding also forces non-critical assets onto the critical path. (e.g images, fonts) 
    - This means that—in this particular case—instead of needing to download 68K of CSS before we can begin rendering the page, we need to download over 3.4× that amount. 
  - Media query images: Base64 encoding forces all asset bytes to be downloaded, even if they’ll never be used. 
  - Base64 encoding restricts our ability to cache assets individually. 
    - images and fonts are now bound to the same caching rules as our styles, and vice versa.
    - CSS change frequently, font almost never change