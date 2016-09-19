# Introduction
A traversal represents one (and only one) path through vGraph, with any associated data it picks up along the way. When a traversal encounters a step where it can follow two paths, the traversal splits into two, each copy following one path. If a traversal encounters a boundary node, the traversal is transfered to the other repository and continues on.

## Simple Traversal (1 path)

**We start on a Node**

![](img/simple-1.png)

**We follow an Edge to an adjacent Node**

![](img/simple-2.png)

**We stop when we're done**

![](img/simple-3.png)

## Branching Traversal

**If we have a running traversal**

![](img/branching-1.png)

**We proceeds normally until we encounter a branch**

![](img/branching-2.png)

**We then copy the traversal and follow both branches**

![](img/branching-3.png)

## Back Tracking Traversal

**Anytime during a traversal**

![](img/backtracking-1.png)

**We can mark our spot and take one path**

![](img/backtracking-2.png)

**We can then return to the spot we marked**

![](img/backtracking-3.png)

**And take a different path**

![](img/backtracking-4.png)

## Cross-Repository Traversal

**Anytime during a traversal**

![](img/cross-repo-1.png)

**If we hit a boundary node**

![](img/cross-repo-2.png)

**We transfer the traversal over to the other repository**

![](img/cross-repo-3.png)

**And we continue our traversal**

![](img/cross-repo-4.png)
