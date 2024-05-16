---
title: Obsidian Markdown Guide
tags:
  - markdown
  - obsidian
  - guide
  - howto
  - tutorial
date: 2024-05-16
---
# Obsidian Markdown Guide

Using Markdown in Obsidian is a bit different from the default usual Markdown that you may be used to. Obsidian supports a variety of extra syntactical features to Markdown that make creating content even easier. 

In the guide, we will go over the nuances and new features that Obsidian brings to our Markdown experience. We will begin our journey with callouts.

## Callouts
These are similar to Markdown quotes that you may have been used to, but with an added syntax to the first line of a quote allows us to format the "quote", in many different ways. 

Starting off with the most basic `info` callout.
```
> [!info]
> Here is some special info!
```

Which looks like this rendered with Obsidian. 
> [!info]
> Here is some special info!

Moving on we have the `tip` callout.
```
> [!tip]
> Here's a great tip.
```

And again rendered with Obsidian.
> [!tip]
> Here's a great tip.

Notice how we always change the keyword within the first line of the quote to change the styling. That's how all of them work. Here's showcase of the 12 supported callouts (excluding Info & Tip as they are above).

### Showcase
> [!note]
> This is a `note`. Use the `note` keyword in the first line of the quote.

> [!summary]
> This is a `summary`. You can also use the aliases `tldr` & `abstract`

> [!todo]
> This is a `todo` item.

> [!tip]
> This is a `tip`. You may also use the aliases `hint` & `important`

> [!success]
> Aliases: `succcess`, `check`, `done`

> [!question]
> Aliases: `question`, `help`, `faq`

> [!warning]
> Aliases: `warning`, `attention`, `caution`

> [!failure]
> Aliases: `failure`, `missing`, `fail`

> [!danger]
> Aliases: `danger`, `error`

> [!bug]
> This is a `bug`

> [!example]
> This is an `example`

> [!quote]
> Aliases: `quote` & `cite`


### Nested Callouts
Yes! We can nest our callouts! Even multiple nesting is supported!!

> [!question] Can we nest our callouts?
> > [!success] Yes we can!!
> > > [!note] We can even do multiple layers like this!

> [!question]- What about collapsing?
> > [!success] Of course!!

> [!question]- What type of content can we put in a callout?
> **Any Markdown**!!
> We can even use sections, and titles. 
> # Big Title
> ## Smaller Title
> Any markdown is valid inside a callout! 
> That means that we can use `code` tags, or even whole snippets!
> ```C
> int main() {
>     return 0;
> }
> ```






 



