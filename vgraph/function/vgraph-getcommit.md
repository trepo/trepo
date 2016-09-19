# getCommit(ID)
Get a Commit.

## Parameters

* [ID](../definition/commit-id.md) - The Commit ID.

## Actions

1. If [ID](../definition/commit-id.md) is invalid, [Error](../definition/error.md).
1. If [Commit](../definition/commit.md) identified by [ID](../definition/commit-id.md) does not exist, [Error](../definition/error.md).

## Returns

The [Commit](../definition/commit.md).