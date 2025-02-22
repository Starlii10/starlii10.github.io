---
layout: post
title: "Template"
categories: site
author: "Starlii"
---

This is a template for Markdown in Jekyll. Neat, huh?

# Header 1

## Header 2

### Header 3

Yeah, this supports basically all Markdown features. Best part: it also supports *images* on the web server!
Just gotta go to **\{\{ site.baseurl \}\}/images/whatever_you_want!** Everything else is standard Markdown. Want an example?

![Starletta]({{ site.baseurl }}/images/starlii_melo.png)

That's a little big. Can't modify size, though...

I can even post my Python code here! Here's a snippet of Vivia's code.

```python
async def version(ctx: commands.Context):
    await ctx.send(personalityMessage("base.version").replace("{version}", __VERSION__), ephemeral=True)
```

> [!TIP]
> AFAIK there's no way to make Markdown alerts in the style of documentation with Jekyll. Sad...
