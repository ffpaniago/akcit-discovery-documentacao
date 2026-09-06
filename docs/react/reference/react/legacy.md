---
title: "legacy.md"
source: https://react.dev/reference/react/legacy.md
captured_at: 2026-09-06T13:03:26.059Z
---


<Intro>

These APIs are exported from the `react` package, but they are not recommended for use in newly written code. See the linked individual API pages for the suggested alternatives.

</Intro>

---

## Legacy APIs {/*legacy-apis*/}

* [`Children`](reference/react/children.md) lets you manipulate and transform the JSX received as the `children` prop. [See alternatives.](reference/react/children.md)
* [`cloneElement`](reference/react/cloneelement.md) lets you create a React element using another element as a starting point. [See alternatives.](reference/react/cloneelement.md)
* [`Component`](reference/react/component.md) lets you define a React component as a JavaScript class. [See alternatives.](reference/react/component.md)
* [`createElement`](reference/react/createelement.md) lets you create a React element. Typically, you'll use JSX instead.
* [`createRef`](reference/react/createref.md) creates a ref object which can contain arbitrary value. [See alternatives.](reference/react/createref.md)
* [`forwardRef`](reference/react/forwardref.md) lets your component expose a DOM node to parent component with a [ref.](learn/manipulating-the-dom-with-refs.md)
* [`isValidElement`](reference/react/isvalidelement.md) checks whether a value is a React element. Typically used with [`cloneElement`.](reference/react/cloneelement.md)
* [`PureComponent`](reference/react/purecomponent.md) is similar to [`Component`,](reference/react/component.md) but it skip re-renders with same props. [See alternatives.](reference/react/purecomponent.md)

---

## Removed APIs {/*removed-apis*/}

These APIs were removed in React 19:

* [`createFactory`](https://18.react.dev/reference/react/createFactory): use JSX instead.
* Class Components: [`static contextTypes`](https://18.react.dev//reference/react/Component#static-contexttypes): use [`static contextType`](#static-contexttype) instead.
* Class Components: [`static childContextTypes`](https://18.react.dev//reference/react/Component#static-childcontexttypes): use [`static contextType`](#static-contexttype) instead.
* Class Components: [`static getChildContext`](https://18.react.dev//reference/react/Component#getchildcontext): use [`Context`](reference/react/createcontext.md) instead.
* Class Components: [`static propTypes`](https://18.react.dev//reference/react/Component#static-proptypes): use a type system like [TypeScript](https://www.typescriptlang.org/) instead.
* Class Components: [`this.refs`](https://18.react.dev//reference/react/Component#refs): use [`createRef`](reference/react/createref.md) instead.

---

## Sitemap

[Overview of all docs pages](llms-txt.md)
