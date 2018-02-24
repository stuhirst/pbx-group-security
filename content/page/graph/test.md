---
title  : Testing Dot Language using viz js
type   : graph
layout : graph-dot-2


nodes:
    - a
    - b
    - c
    - d
    - e
    - f
---

dinetwork {
    node[shape=box];
    
    1 -> -1 -> 2;
    2 -> 3; 
    2 -- 4; 
    2 -> 1 -> AAAA -> BBBB
    3 -> 5 [shape=circle]; 
    node "This is a node" [shape=square, color =red]
}
