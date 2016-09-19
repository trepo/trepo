# Commit Prev
The [Commit ID](commit-id.md) of the [Commit](commit.md) immediately preceding this [Commit](commit.md). If this [Commit](commit.md) is the first commit in vGraph, then the value of `prev` will be null.

When patching vGraph, if the value of prev does not match the current commit id, an error is thrown. To allow commits coming from another instance of vGraph to be pathed, [vGraph.merge()](../function/vgraph-merge.md) may be used to reformat the commit.