# copy(Author, Email, Message, [Nodes])
Copy all or part of the graph. Note that this does NOT preserve history.

## Parameters

* [Author](../definition/commit-author.md) - The author of this Commit.
* [Email](../definition/commit-email.md) - The email of the author of this Commit.
* [Message](../definition/commit-message.md) - The message associated with this Commit.
* [Nodes](../definition/element-id.md) - An (optional) array of Node IDs.

## Actions

1. If [Author](../definition/commit-author.md), [Email](../definition/commit-email.md), [Message](../definition/commit-message.md), or any ID in [Nodes](../definition/element-id.md) is invalid, [Error](../definition/error.md).
1. If there are uncommitted changes, [Error](../definition/error.md).
1. Create a new [Commit](../definition/commit.md).
    * Set [id](../definition/commit-id.md) to a new [UUIDv4](../definition/uuidv4)
    * Set [prev](../definition/commit-prev.md) to Null.
    * Set [timestamp](../definition/commit.md) to a new [Timestamp](../definition/timestamp.md).
    * Set [repo](../definition/commit.md) to the [vGraph Repo](../definition/repo.md).
    * Set [author](../definition/commit-author.md).
    * Set [email](../definition/commit-email.md).
    * Set [message](../definition/commit-message.md).
1. If [Nodes](../definition/element-id.md) is NOT set:
    1. For each [Node](../definition/node.md) in the graph:
        1. If [Node](../definition/node.md) is a [Boundary Node](../definition/boundary-node.md), create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
            * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
            * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
            * Set [action](../definition/commit-action.md) to `create`.
            * Set [boundary](../definition/commit-boundary.md) to `true`.
            * Set [repo](../definition/commit.md) to the [Node's Repo](../definition/node-repo.md).
        1. Else create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
            * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
            * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
            * Set [action](../definition/commit-action.md) to `create`.
            * Set [boundary](../definition/commit-boundary.md) to `false`.
            * Set [props](../definition/commit.md) to the [Node's Properties](../definition/element-properties.md).
    1. For each [Edge](../definition/edge.md) in the graph:
        1. Create [Edge for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
            * Set [id](../definition/commit.md) to the [Edge's ID](../definition/element-id.md).
            * Set [label](../definition/commit.md) to the [Edge's Label](../definition/element-label.md).
            * Set [from](../definition/commit.md) to the [Edge's From Node ID](../definition/edge.md).
            * Set [to](../definition/commit.md) to the [Edge's To Node ID](../definition/edge.md).
            * Set [action](../definition/commit-action.md) to `create`.
            * Set [props](../definition/commit.md) to the [Edge's Properties](../definition/element-properties.md).
1. Else:
    1. Create an array of [Node IDs](../definition/element-id.md) called `Nodes Touched`.
    1. For each [Node](../definition/node.md) in [Nodes](../definition/element-id.md):
        1. If [Node](../definition/node.md) is a [Boundary Node](../definition/boundary-node.md), create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
            * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
            * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
            * Set [action](../definition/commit-action.md) to `create`.
            * Set [boundary](../definition/commit-boundary.md) to `true`.
            * Set [repo](../definition/commit.md) to the [Node's Repo](../definition/node-repo.md).
        1. Else create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
            * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
            * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
            * Set [action](../definition/commit-action.md) to `create`.
            * Set [boundary](../definition/commit-boundary.md) to `false`.
            * Set [props](../definition/commit.md) to the [Node's Properties](../definition/element-properties.md).
        1. For each [Edge](../definition/edge.md) connected to [Node](../definition/node.md) that is NOT in the [Commit](../definition/commit.md):
            1. Create [Edge for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
                * Set [id](../definition/commit.md) to the [Edge's ID](../definition/element-id.md).
                * Set [label](../definition/commit.md) to the [Edge's Label](../definition/element-label.md).
                * Set [from](../definition/commit.md) to the [Edge's From Node ID](../definition/edge.md).
                * Set [to](../definition/commit.md) to the [Edge's To Node ID](../definition/edge.md).
                * Set [action](../definition/commit-action.md) to `create`.
                * Set [props](../definition/commit.md) to the [Edge's Properties](../definition/element-properties.md).
            1. If [Edge](../definition/edge.md) is coming TO this [Node](../definition/node.md), add [Edge's From Node ID](../definition/edge.md) to `Nodes Touched`.
            1. If [Edge](../definition/edge.md) is going FROM this [Node](../definition/node.md), add [Edge's TO Node ID](../definition/edge.md) to `Nodes Touched`.
    1. For each [Node ID](../definition/element-id.md) in `Nodes Touched`:
        1. If [Node](../definition/node.md) identified by [Node ID](../definition/element-id.md) is NOT in the [Commit](../definition/commit.md), create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
            * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
            * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
            * Set [action](../definition/commit-action.md) to `create`.
            * Set [boundary](../definition/commit-boundary.md) to `true`.
            * Set [repo](../definition/commit.md) to [vGraph's Repo](../definition/repo.md).

## Returns

The [Commit](../definition/commit.md).