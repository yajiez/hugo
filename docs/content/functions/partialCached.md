---
title: partialCached
linktitle: partialCached
description: Allows for caching of partials that do not need to be re-rendered on every invocation.
godocref:
date: 2017-02-01
publishdate: 2017-02-01
lastmod: 2017-02-01
categories: [functions]
menu:
  docs:
    parent: "functions"
#tags: []
signature: ["partialCached LAYOUT INPUT [VARIANT...]"]
workson: []
hugoversion:
relatedfuncs: []
deprecated: false
aliases: []
---

The `partialCached` template function can offer significant performance gains for complex templates that don't need to be re-rendered on every invocation. Here is the simplest usage:

```golang
{{ partialCached "footer.html" . }}
```

You can also pass additional parameters to `partialCached` to create *variants* of the cached partial. For example, if you have a complex partial that should be identical when rendered for pages within the same section, you could use a variant based upon section so that the partial is only rendered once per section:

{{% code file="partial-cached-example.html" %}}
```
{{ partialCached "footer.html" . .Section }}
```
{{% /code %}}

If you need to pass additional parameters to create unique variants, you can pass as many variant parameters as you need:

```
{{ partialCached "footer.html" . .Params.country .Params.province }}
```

Note that the variant parameters are not made available to the underlying partial template. They are only use to create a unique cache key.
