---
title  : "MarkDown Newbie"
author : Harrie Bickle
date   : "2018-02-02"
tags   : ["Markdown", "GitHub"]
categories: ["HowTo"]
notes:
 - edited
 - reviewed
---


# The future is here and it is written in markdown.

If you care more about content than code, and you understand that it is the words that count, then markdown is here for you.

In my opinion syntax is a pain. Some people are naturals and perfection flows from their fingertips. I am more the "need to be reminded to try for perfect" type. Fixing syntax errors feels like a constant nudge from someone whilst you are trying to concentrate on something more important.

A great example of the "excision of faffing around" that markdown excels at is probably this:


Do you want to create an external link? Then put it in your document:

```
https://www.easypeasy.com
```
https://www.easypeasy.com

and say farewell to all that fussing around with ", his perfectly-placed friend / and the `<a>`  gang.

```
<a href="http://devil_in_the_detail.com">link to site here</a>
```

## Want a header? 

No ```<h1>wrapper</h1>```needed:

```
# H1
## H2
### H3

```
The "#" is all you need, you can use up to 6 of them.

# H1
## H2
### H3

## Need an image? 
(Sorry, you do still need to have / around for this one, some details really do matter).

```

![imageDescription](https://yourdomain.com/img/name.jpg) imageLegend

```
![image of dandelions](/img/blog.jpg) image of dandelions


## Tables can be built with pipes and formatted with colons:

```

| Tables    | Are                  | Easy    |
| ------------------- |:-------------------: | ----:   |
| Right hand column   | right-aligned        | 10,000  |
| Middle column       | centered             | 10      |
| laces               | are neat             | 2       |

```



| Tables             | Are                  | Easy    |
| ------------------ |:-------------------: | ----:   |
| Right hand column  | right-aligned        | 10,000  |
|Middle column       | centered             | 10      |
| laces              | are neat             | 2       |

You get away with writing less syntax that is way more reader-friendly, and a bit of software converts your text into HTML following your gentle hints.

That's pretty awesome you say? Indeed it is, and this site itself is a great example of markdown in action. Hugo runs some Perl to render your files as HTML, and you can let the software worry about those fiddly details.

## Resources

[Cheat Sheet](https://help.github.com/articles/basic-writing-and-formatting-syntax/)

[Hugo Help](https://gohugo.io/content-management/formats/#learn-markdown)

[Interactive Tutorial](https://www.markdowntutorial.com/lesson/1/)

[Go deeper](https://daringfireball.net/projects/markdown/)
