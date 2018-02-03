---
draft  : true
title  : MarkDown Newbie
author : Harrie Bickle
notes:
 - draft0
 - plenty to do to make sure intended md renders and that example markdown does not
---

Markdown on Hugo

So there you are, you put in the time and got your XML sorted, no anchor tag is going to trip you up. Brain section 89/r16/2 filled to capacity with syntax, then some dreamer goes and takes it all away.

The future is here and it is markdown.

In my opinion Syntax is a pain in the ass. Some people are good, perfection flows from their finger tips. I am more the "need to be reminded to try for perfect" type. Syntax errors feel like a constant nudge from someone whilst you are trying to concentrate on something more important.

A great example of the "excision of faffing around" that markdown excels at is probably this:

[//]: # ha in WP I have a text box for visual effect http://www.technobunnies.com/technical/markdown/

Put the mat out for:

"(https://www.easypeasy.com)"

and say farewell to all that fussing around with " and his perfectly-placed friend /.

<a href="http://devil_in_the_detail.com">link to site here</a>

Want a header? No wrapper needed:
``` # H1
## H2
### H3
```

# H1
## H2
### H3

Need an image? (Sorry you do still need to have " and / around for this one, some details really do matter).
[logo]: https://mylogo.com/icon232.png "Logo Title"

| Tables    | Are           | Easy    |
| --------- |:-------------:| ----:   |
| 10,000 is | right-aligned | 10,000  |
| 10 is     | centered      | 10      |
| laces     | are neat      | 2       |


[//]: # probably going to have to take an image of the table to present the non-renered version

Colons can be used to align columns.
Tables	Are	Cool
RHS Column is	right-aligned	10,000
Middle/Column 2 is	centered	10
laces	are neat	2


You get away with writing less syntax, that is way more reader friendly and a bit of software converts your text into HTML following your gentle hints.

That's pretty awesome you say? Indeed it is, that is what this site is written in.

Resources

[GitHub Cheat Sheet] (https://help.github.com/articles/basic-writing-and-formatting-syntax/)

(https://daringfireball.net/projects/markdown/)

[Markdown in Hugo] (https://gohugo.io/content-management/formats/#learn-markdown)

[Interactive tutorial] (https://www.markdowntutorial.com/lesson/1/)
