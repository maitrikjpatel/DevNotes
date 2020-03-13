---
date: '2020-3-12'
publish: 'false'
category: 'note'
author: 'Maitrik Patel'

title: 'Web Performance'
description: 'Most users rate speed as being at the very top of the UX hierarch'

topics: 'tools, development'

source: 'Github'
---


### Articles


### Topics and case studies

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