# addBoundary(ID, Label, Repo)
Add a Boundary Node.

## Parameters

* [ID](../definition/element-id.md) - The ID.
* [Label](../definition/element-label.md) - The Label.
* [Repo](../definition/repo.md) - The Repo.

## Actions

1. If [ID](../definition/element-id.md) is invalid, [Error](../definition/error.md).
1. If [Label](../definition/element-label.md) is invalid, [Error](../definition/error.md).
1. If [Repo](../definition/repo.md) is invalid, [Error](../definition/error.md).
1. If [Repo](../definition/node-repo.md) is the same as [vGraph Repo](../definition/repo.md), [Error](../definition/error.md).
1. If [Node](../definition/node.md) identified by [ID](../definition/element-id.md) exists, [Error](../definition/error.md).
1. Create a new [Node](../definition/node.md)
    * Set [ID](../definition/element-id.md).
    * Set [Label](../definition/element-label.md).
    * Set [Repo](../definition/repo.md).
    * Set [Status](../definition/element-status.md) to `1`.

## Returns

The new [Boundary Node](../definition/boundary-node.md).