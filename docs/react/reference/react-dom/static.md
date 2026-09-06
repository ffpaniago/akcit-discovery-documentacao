---
title: "static.md"
source: https://react.dev/reference/react-dom/static.md
captured_at: 2026-09-06T13:02:53.889Z
---


<Intro>

The `react-dom/static` APIs let you generate static HTML for React components. They have limited functionality compared to the streaming APIs. A [framework](learn/creating-a-react-app.md) may call them for you. Most of your components don't need to import or use them.

</Intro>

---

## Static APIs for Web Streams {/*static-apis-for-web-streams*/}

These methods are only available in the environments with [Web Streams](https://developer.mozilla.org/en-US/docs/Web/API/Streams_API), which includes browsers, Deno, and some modern edge runtimes:

* [`prerender`](reference/react-dom/static/prerender.md) renders a React tree to static HTML with a [Readable Web Stream.](https://developer.mozilla.org/en-US/docs/Web/API/ReadableStream)
* [`resumeAndPrerender`](reference/react-dom/static/resumeandprerender.md) continues a prerendered React tree to static HTML with a [Readable Web Stream](https://developer.mozilla.org/en-US/docs/Web/API/ReadableStream).

Node.js also includes these methods for compatibility, but they are not recommended due to worse performance. Use the [dedicated Node.js APIs](#static-apis-for-nodejs-streams) instead.

---

## Static APIs for Node.js Streams {/*static-apis-for-nodejs-streams*/}

These methods are only available in the environments with [Node.js Streams](https://nodejs.org/api/stream.html):

* [`prerenderToNodeStream`](reference/react-dom/static/prerendertonodestream.md) renders a React tree to static HTML with a [Node.js Stream.](https://nodejs.org/api/stream.html)
* [`resumeAndPrerenderToNodeStream`](reference/react-dom/static/resumeandprerendertonodestream.md) continues a prerendered React tree to static HTML with a [Node.js Stream.](https://nodejs.org/api/stream.html)


---

## Sitemap

[Overview of all docs pages](llms-txt.md)
