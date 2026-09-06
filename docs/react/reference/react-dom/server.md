---
title: "server.md"
source: https://react.dev/reference/react-dom/server.md
captured_at: 2026-09-06T13:02:48.281Z
---


<Intro>

The `react-dom/server` APIs let you server-side render React components to HTML. These APIs are only used on the server at the top level of your app to generate the initial HTML. A [framework](learn/creating-a-react-app.md) may call them for you. Most of your components don't need to import or use them.

</Intro>

---

## Server APIs for Web Streams {/*server-apis-for-web-streams*/}

These methods are only available in the environments with [Web Streams](https://developer.mozilla.org/en-US/docs/Web/API/Streams_API), which includes browsers, Deno, and some modern edge runtimes:

* [`renderToReadableStream`](reference/react-dom/server/rendertoreadablestream.md) renders a React tree to a [Readable Web Stream.](https://developer.mozilla.org/en-US/docs/Web/API/ReadableStream)
* [`resume`](reference/react-dom/server/resume.md) resumes [`prerender`](reference/react-dom/static/prerender.md) to a [Readable Web Stream](https://developer.mozilla.org/en-US/docs/Web/API/ReadableStream).


<Note>

Node.js also includes these methods for compatibility, but they are not recommended due to worse performance. Use the [dedicated Node.js APIs](#server-apis-for-nodejs-streams) instead.

</Note>
---

## Server APIs for Node.js Streams {/*server-apis-for-nodejs-streams*/}

These methods are only available in the environments with [Node.js Streams:](https://nodejs.org/api/stream.html)

* [`renderToPipeableStream`](reference/react-dom/server/rendertopipeablestream.md) renders a React tree to a pipeable [Node.js Stream.](https://nodejs.org/api/stream.html)
* [`resumeToPipeableStream`](reference/react-dom/server/resumetopipeablestream.md) resumes [`prerenderToNodeStream`](reference/react-dom/static/prerendertonodestream.md) to a pipeable [Node.js Stream.](https://nodejs.org/api/stream.html)

---

## Legacy Server APIs for non-streaming environments {/*legacy-server-apis-for-non-streaming-environments*/}

These methods can be used in the environments that don't support streams:

* [`renderToString`](reference/react-dom/server/rendertostring.md) renders a React tree to a string.
* [`renderToStaticMarkup`](reference/react-dom/server/rendertostaticmarkup.md) renders a non-interactive React tree to a string.

They have limited functionality compared to the streaming APIs.

---

## Sitemap

[Overview of all docs pages](llms-txt.md)
