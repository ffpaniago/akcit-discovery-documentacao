---
title: "apis.md"
source: https://react.dev/reference/react/apis.md
captured_at: 2026-09-06T13:02:17.659Z
---


<Intro>

In addition to [Hooks](reference/react/hooks.md) and [Components](reference/react/components.md), the `react` package exports a few other APIs that are useful for defining components. This page lists all the remaining modern React APIs.

</Intro>

---

* [`createContext`](reference/react/createcontext.md) lets you define and provide context to the child components. Used with [`useContext`.](reference/react/usecontext.md)
* [`lazy`](reference/react/lazy.md) lets you defer loading a component's code until it's rendered for the first time.
* [`memo`](reference/react/memo.md) lets your component skip re-renders with same props. Used with [`useMemo`](reference/react/usememo.md) and [`useCallback`.](reference/react/usecallback.md)
* [`startTransition`](reference/react/starttransition.md) lets you mark a state update as non-urgent. Similar to [`useTransition`.](reference/react/usetransition.md)
* [`act`](reference/react/act.md) lets you wrap renders and interactions in tests to ensure updates have processed before making assertions.
* [`cache`](reference/react/cache.md) lets you cache the result of a data fetch or computation.
* [`cacheSignal`](reference/react/cachesignal.md) lets you know when the `cache()` lifetime is over.
* [`captureOwnerStack`](reference/react/captureownerstack.md) reads the current Owner Stack in development and returns it as a string if available.

---

## Resource APIs {/*resource-apis*/}

*Resources* can be accessed by a component without having them as part of their state. For example, a component can read a message from a Promise or read styling information from a context.

You can pass these types of resources to [`use`](reference/react/use.md):

* A [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) to read its resolved value.
* A [context](learn/passing-data-deeply-with-context.md) to read its value.
* <CanaryBadge /> The value returned by [`browser`](reference/react-dom/browser.md) to mark a component as browser-only during server rendering.

```js
function MessageComponent({ messagePromise }) {
  const message = use(messagePromise);
  const theme = use(ThemeContext);
  use(browser());
  // ...
}
```

---

## Sitemap

[Overview of all docs pages](llms-txt.md)
