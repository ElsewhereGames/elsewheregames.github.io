---
published: true
layout: post
tags: 
  - "c#"
  - "code-as-a-craft"
excerpt: "I check `using` directives as an indicator of code quality."
---

## I Don't Trust Your C# Code When...

When reading someone else's code, I get suspicious when the first set of `using` directives are the defaults:
{% highlight csharp %}
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
{% endhighlight %}

Technically this isn't really a problem, code only gets pulled in as needed, but leaving the defaults indicates to me that the orignal developer either doesn't see programming as a [craft](http://manifesto.softwarecraftsmanship.org/) or was rushed for time.