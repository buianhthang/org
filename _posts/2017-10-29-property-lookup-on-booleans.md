---
layout: post
title: "Property lookup on booleans"
description: "Property lookup on booleans"
keywords: ""
date: 2017-10-29
comments: false
categories: tip trick
external-url: https://github.com/babel/babel/commit/1c0a8eb14b69cca00aa96db65b69d0848013c680
permalink: 2017/10/29/property-lookup-on-booleans
---

> Performs a lot of dynamic lookups on the `Boolean.prototype`, as the *ToBoolean* operation let's `true` pass for `obj` (which might itself be concerning that this can be a boolean). Instead of the coercion, the code should properly check for valid objects via `typeof` and strict equality with `null` comparison.

#### Example:

Use below

```js
if (typeof obj === "object" && obj !== null) {
    return obj[key] || 0
}

return 0
 ```
Instead of
```js
return (obj && obj[key]) || 0
```