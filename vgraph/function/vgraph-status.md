# status([Author, Email, Message])
Get a Commit representing the uncommitted changes.

## Parameters

* [Author](../definition/commit-author.md) - The author of this Commit.
* [Email](../definition/commit-email.md) - The email of the author of this Commit.
* [Message](../definition/commit-message.md) - The message associated with this Commit.

## Actions
**Note:** Note that nodes MUST be processed before edges so that reference nodes are added AFTER all regular nodes have been added to the Commit.

1. Create a new [Commit](../definition/commit.md).
    * Set [id](../definition/commit-id.md) to a new [UUIDv4](../definition/uuidv4)
    * Set [prev](../definition/commit-prev.md) to the most recent [Commit ID](../definition/commit-id.md) or `Null` if this is the first [Commit](../definition/commit.md).
    * Set [timestamp](../definition/commit.md) to a new [Timestamp](../definition/timestamp.md).
    * Set [repo](../definition/commit.md) to the [vGraph Repo](../definition/repo.md).
    * Set [author](../definition/commit-author.md).
    * Set [email](../definition/commit-email.md).
    * Set [message](../definition/commit-message.md).
1. For each [Node](../definition/node.md) where [Status](../definition/element-status.md) is greater than `0` (Changed):
    1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted):
        1. If [Status](../definition/element-status.md) is equal to `4` (Clean Delete):
            1. If [Repo](../definition/node-repo.md) is set, create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
                * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
                * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
                * Set [action](../definition/commit-action.md) to `delete`.
                * Set [boundary](../definition/commit-boundary.md) to `true`.
                * Set [origRepo](../definition/commit.md) to the [Node's Repo](../definition/node-repo.md).
            1. Else create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
                * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
                * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
                * Set [action](../definition/commit-action.md) to `delete`.
                * Set [boundary](../definition/commit-boundary.md) to `false`.
                * Set [origProps](../definition/commit.md) to the [Node's Properties](../definition/element-properties.md).
        1. Else If [Status](../definition/element-status.md) is equal to `6` (Update Delete):
            1. If [Node's Original Properties](../definition/element-original-properties.md) are set, create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
                * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
                * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
                * Set [action](../definition/commit-action.md) to `delete`.
                * Set [boundary](../definition/commit-boundary.md) to `false`.
                * Set [origProps](../definition/commit.md) to the [Node's Original Properties](../definition/element-original-properties.md).
            1. Else create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
                * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
                * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
                * Set [action](../definition/commit-action.md) to `delete`.
                * Set [boundary](../definition/commit-boundary.md) to `true`.
                * Set [origRepo](../definition/commit.md) to the [Node's Original Repo](../definition/node-original-repo.md).
        1. Else [Status](../definition/element-status.md) is equal to `5` or `7` (Create Delete), remove [Node](../definition/node.md). Nodes that are created and deleted in the same commit do not exist.
    1. Else if [Status](../definition/element-status.md) equals `2` (Updated):
        1. If [Repo](../definition/node-repo.md) is set:
            1. If [Node's Original Properties](../definition/element-original-properties.md) are set, create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
                * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
                * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
                * Set [action](../definition/commit-action.md) to `update`.
                * Set [boundary](../definition/commit-boundary.md) to `true`.
                * Set [repo](../definition/commit.md) to the [Node's Repo](../definition/node-repo.md).
                * Set [origProps](../definition/commit.md) to the [Node's Original Properties](../definition/element-original-properties.md).
            1. Else create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
                * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
                * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
                * Set [action](../definition/commit-action.md) to `update`.
                * Set [boundary](../definition/commit-boundary.md) to `true`.
                * Set [repo](../definition/commit.md) to the [Node's Repo](../definition/node-repo.md).
                * Set [origRepo](../definition/commit.md) to the [Node's Original Repo](../definition/node-original-repo.md).
        1. Else:
            1. If [Node's Original Properties](../definition/element-original-properties.md) are set, create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
                * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
                * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
                * Set [action](../definition/commit-action.md) to `update`.
                * Set [boundary](../definition/commit-boundary.md) to `false`.
                * Set [props](../definition/commit.md) to the [Node's Properties](../definition/element-properties.md).
                * Set [origProps](../definition/commit.md) to the [Node's Original Properties](../definition/element-original-properties.md).
            1. Else create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
                * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
                * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
                * Set [action](../definition/commit-action.md) to `update`.
                * Set [boundary](../definition/commit-boundary.md) to `false`.
                * Set [props](../definition/commit.md) to the [Node's Properties](../definition/element-properties.md).
                * Set [origRepo](../definition/commit.md) to the [Node's Original Repo](../definition/node-original-repo.md).
    1. Else [Status](../definition/element-status.md) status equals `1` or `3` (Created):
        1. If [Repo](../definition/node-repo.md) is set, create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
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
1. For each [Edge](../definition/edge.md) where [Status](../definition/element-status.md) is greater than `0` (Changed):
    1. If [Status](../definition/element-status.md) does NOT equal `5` or `7` (Create Delete):
        1. If [Edge's From Node](../definition/edge.md) is NOT present in the [Commit](../definition/commit.md), create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
            * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
            * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
            * Set [action](../definition/commit-action.md) to `reference`.
            * Set [boundary](../definition/commit-boundary.md) to `true`.
            * Set [repo](../definition/commit.md) to [Node's Repo](../definition/node-repo.md) if set, [vGraph's Repo](../definition/repo.md) otherwise.
        1. If [Edge's To Node](../definition/edge.md) is NOT present in the [Commit](../definition/commit.md), create [Node for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
            * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
            * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
            * Set [action](../definition/commit-action.md) to `reference`.
            * Set [boundary](../definition/commit-boundary.md) to `true`.
            * Set [repo](../definition/commit.md) to [Node's Repo](../definition/node-repo.md) if set, [vGraph's Repo](../definition/repo.md) otherwise.
    1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted):
        1. If [Status](../definition/element-status.md) is equal to `4` (Clean Delete), create [Edge for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
            * Set [id](../definition/commit.md) to the [Edge's ID](../definition/element-id.md).
            * Set [label](../definition/commit.md) to the [Edge's Label](../definition/element-label.md).
            * Set [from](../definition/commit.md) to the [Edge's From Node ID](../definition/edge.md).
            * Set [to](../definition/commit.md) to the [Edge's To Node ID](../definition/edge.md).
            * Set [action](../definition/commit-action.md) to `delete`.
            * Set [origProps](../definition/commit.md) to the [Edge's Properties](../definition/element-properties.md).
        1. Else If [Status](../definition/element-status.md) is equal to `6` (Update Delete), create [Edge for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
            * Set [id](../definition/commit.md) to the [Edge's ID](../definition/element-id.md).
            * Set [label](../definition/commit.md) to the [Edge's Label](../definition/element-label.md).
            * Set [from](../definition/commit.md) to the [Edge's From Node ID](../definition/edge.md).
            * Set [to](../definition/commit.md) to the [Edge's To Node ID](../definition/edge.md).
            * Set [action](../definition/commit-action.md) to `delete`.
            * Set [origProps](../definition/commit.md) to the [Edge's Original Properties](../definition/element-original-properties.md).
        1. Else [Status](../definition/element-status.md) is equal to `5` or `7` (Create Delete), remove [Edge](../definition/edge.md). Edges that are created and deleted in the same commit do not exist.
    1. Else if [Status](../definition/element-status.md) equals `2` (Updated), create [Edge for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
        * Set [id](../definition/commit.md) to the [Edge's ID](../definition/element-id.md).
        * Set [label](../definition/commit.md) to the [Edge's Label](../definition/element-label.md).
        * Set [from](../definition/commit.md) to the [Edge's From Node ID](../definition/edge.md).
        * Set [to](../definition/commit.md) to the [Edge's To Node ID](../definition/edge.md).
        * Set [action](../definition/commit-action.md) to `update`.
        * Set [props](../definition/commit.md) to the [Edge's Properties](../definition/element-properties.md).
        * Set [origProps](../definition/commit.md) to the [Edge's Original Properties](../definition/element-original-properties.md).
    1. Else [Status](../definition/element-status.md) status equals `1` or `3` (Created), create [Edge for the Commit](../definition/commit.md) and add it to the [Commit](../definition/commit.md).
        * Set [id](../definition/commit.md) to the [Edge's ID](../definition/element-id.md).
        * Set [label](../definition/commit.md) to the [Edge's Label](../definition/element-label.md).
        * Set [from](../definition/commit.md) to the [Edge's From Node ID](../definition/edge.md).
        * Set [to](../definition/commit.md) to the [Edge's To Node ID](../definition/edge.md).
        * Set [action](../definition/commit-action.md) to `create`.
        * Set [props](../definition/commit.md) to the [Edge's Properties](../definition/element-properties.md).

## Returns

The [Commit](../definition/commit.md).

## Notes

**Commit Action and Edge Properties**

|            | \_\_status | \_\_origProps |
| :--------: | :---------:| :-----------: |
| **Create** | 1,3        |               |
| **Update** | 2          | X             |
| **Delete** | 4+         | ? (1)         |

1. After a Commit, if an Edge is changed and then deleted, `__origProps` will be set.

**Commit Action and Node Properties**

|                           | \_\_status | \_\_repo | \_\_origRepo | \_\_origProps |
| :-----------------------: | :--------: | :------: | :----------: | :-----------: |
| **Create Node**           | 1,3        |          |              |               |
| **Update Node**           | 2          |          |              | X             |
| **Delete Node**           | 4+         |          | ? (1)        | ? (2)         |
| **Create Boundary Node**  | 1,3        | X        |              |               |
| **Update Boundary Node**  | 2          | X        | X            |               |
| **Delete Boundary Node**  | 4+         | X        | ? (3)        | ? (4)         |
| **Boundary Node -> Node** | 2          |          | X            |               |
| **Node -> Boundary Node** | 2          | X        |              | X             |

1. After a Commit, if a Boundary Node is transformed into a Node and then deleted, `__origRepo` will be set. This is committed as a Delete Boundary Node.
2. After a Commit, if a Node is changed and then deleted, `__origProps` will be set.
3. After a Commit, if a Boundary Node is changed and then deleted, `__origRepo` will be set.
4. After a Commit, if a Node is transformed into a Boundary Node and then deleted, `__origProps` will be set. This is committed as a Delete Node.
