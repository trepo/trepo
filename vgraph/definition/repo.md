# Repo
The repository identifier. This is typically a URI (e.g., https://example.com/repository) pointing to the root of a Trepo Instance. In practice, this should be a resolvable URL.

The value of Repo is stored in the [Root Node](../graph/root-node.md) of vGraph, and in the property [__repo](../graph/node.md) for (Boundary Nodes)(boundary-node.md).

## Requirements
The repo must match the regex `.{1,254}`.