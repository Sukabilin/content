---
title: Vary
slug: Web/HTTP/Headers/Vary
tags:
  - HTTP
  - Reference
  - Response
  - Response Header
  - header
browser-compat: http.headers.Vary
---
{{HTTPSidebar}}

The **`Vary`** HTTP response header determines how to match
future request headers to decide whether a cached response can be used rather than
requesting a fresh one from the origin server. It is used by the server to indicate
which headers it used when selecting a representation of a resource in a [content negotiation](/en-US/docs/Web/HTTP/Content_negotiation) algorithm.

The `Vary` header should be set on a {{HTTPStatus("304")}}
`Not Modified` response exactly like it would have been set on an equivalent
{{HTTPStatus("200")}} `OK` response.

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">Header type</th>
      <td>{{Glossary("Response header")}}</td>
    </tr>
    <tr>
      <th scope="row">{{Glossary("Forbidden header name")}}</th>
      <td>no</td>
    </tr>
  </tbody>
</table>

## Syntax

```html
Vary: *
Vary: <header-name>, <header-name>, ...
```

## Directives

- \*
  - : Each request for a URL is supposed to be treated as a unique and uncacheable
    request. A better way to indicate this is to use {{HTTPHeader("Cache-Control")}}:
    `no-store`, which is clearer to read and also signals that the object
    shouldn't be stored ever.
- \<header-name>
  - : A comma-separated list of header names to take into account when deciding whether or
    not a cached response can be used.

## Examples

### Dynamic serving

When using the `Vary: User-Agent` header, caching servers should consider
the user agent when deciding whether to serve the page from cache. For example, if you
are serving different content to mobile users, it can help you to avoid that a cache may
mistakenly serve a desktop version of your site to your mobile users. It can help Google
and other search engines to discover the mobile version of a page, and might also tell
them that no [Cloaking](https://en.wikipedia.org/wiki/Cloaking) is intended.

    Vary: User-Agent

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## Compatibility notes

- [Vary
  with care – Vary header problems in IE6-9](https://blogs.msdn.microsoft.com/ieinternals/2009/06/17/vary-with-care/)

## See also

- [Understanding
  The Vary Header - Smashing Magazine](https://www.smashingmagazine.com/2017/11/understanding-vary-header/)
- [Best
  Practices for Using the Vary Header – fastly.com](https://www.fastly.com/blog/best-practices-for-using-the-vary-header)
- [Content
  negotiation](/en-US/docs/Web/HTTP/Content_negotiation)