---
draft  : true
title  : Why Visio diagrams don't scale
author : Dinis Cruz
notes:
 - edited
---

Why Visio diagrams don't scale


Visio diagrams have, non-text based or non-dynamic diagrams. This creates key fundamental problems, relegating them to being equivalent to diagrams on a white board or a static file. The first issue, is that they are hard to edit; the user must have Visio installed, or another online diagram tool. They also they require that the person who actually created the diagram in the first place, is the one to maintain it and make changes. 

One of the best features of these diagramming tools, because this does not just apply to Visio, this applies to any of the major online big-set diagramming tools that exist out there; is the fact that you can spend a lot of time improving the design, and create some beautiful, intrinsic designs. However, since each component is manually maintained, sometimes, with a little bit of automation, when you change an object from the other side, the lines, kind of, just stay together.

It's the fact that they are hard coded, right? The patches and the structure are hard coded, making it very hard to make changes. So, it's a situation that, as the team evolves, after a while it becomes very allergic to making changes to the diagrams. A change sometimes implies that your design architecture needs to change. Then the team becomes resistant because they have to register the initial returns. The more complex the graph becomes, the harder it becomes to maintain.

So, that leads to another big problem that you have with these graphs, which is the fact that they tend to be snapshot of a moment in time. This leads to their not being used day to day, which means they go out of date and lose their significance. This creates a situation where you need this massive spike of work just to update them. Which is kind of why most of these graphs, and most of these network graphs, tend to be out of date. This is an issue because they only add value if they are 100% correct, or at least 99% so you can easily make modifications.

We need these graphs to be very easy to change, and they are not. The issues stems from their being hard coded. The alternative is to have dynamically generated graphs, where you can control the layout. This is a powerful feature. Because it's very easy to make change, you are happy to make change, because you don't pay the cost of actually having to restructure everything across the board.

Okay, so, what is this dynamic alternative? The alternative is to use technology like a dot language and tools like Graphviz to generate graphs from text, or programmatically from script. This uses an environment, where the data source that is used to create your graph is dynamic, and as the data updates you graph changes. Your graph is more defined, your graph takes different shapes and different structures. It also scales, because you can actually start to use those graphs and those structures in your day to day, especially if you can get it to the point where they are managed in a git environment. You must also solve, the other big problem, which is versioning. Which is basically the fact that you want something to be easy to edit, but also easy to see the differences between one graph to the other.

So, we need to add another big problem that graphs have is versioning. Another big challenge that we have, especially with big graphs and the more complex they become, it that it's very hard to version, which means that when you look at it overtime, not only they might not be updated, when you look at a graph a week later, or a month later, what you really want to see is the delta. What you really want to understand is what changed from the last time you saw this graph and, unless the data is stored, for example in a text based format, or in a way that it's easy to differentiate, then you can actually not tell the difference. And that becomes again a big problem.

So, the reason I like technologies like dot language and others, is because they create the environment in which modifications are simple, data updates are automatic and versioning is retained.
