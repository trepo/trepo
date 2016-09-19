# merge(Commit)
Reformat a Commit for this graph.

**Note:** If you do not want any of the default reformats to take place, just create a new Commit beforehand with the changes you want.

## Parameters

* [Commit](../definition/commit.md) - The commit to reformat.

## Actions

1. If [Commit](../definition/commit.md) is invalid, [Error](../definition/error.md).
1. If there are uncommitted changes, [Error](../definition/error.md).
1. Create a set of [Node IDs](../definition/element-id.md) called `References To Create`.
1. Create a [New Commit](../definition/commit.md).
    * Set [id](../definition/commit-id.md) to a new [UUIDv4](../definition/uuidv4)
    * Set [prev](../definition/commit-prev.md) to the most recent [Commit ID](../definition/commit-id.md) or `Null` if this is the first [Commit](../definition/commit.md).
    * Set [timestamp](../definition/commit.md) to a new [Timestamp](../definition/timestamp.md).
    * Set [repo](../definition/commit.md) to the [Commit's Repo](../definition/commit.md).
    * Set [author](../definition/commit-author.md) to the [Commit's Author](../definition/commit.md).
    * Set [email](../definition/commit-email.md) to the [Commit's Email](../definition/commit.md).
    * Set [message](../definition/commit-message.md) to the [Commit's Message](../definition/commit.md).
1. For each [Commit's Edge](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `create` or `update`:
    1. Add [Edge's From ID](../definition/element-id.md) to `References To Create`.
    1. Add [Edge's To ID](../definition/element-id.md) to `References To Create`.
    1. If [Edge](../definition/edge.md) is present in the graph, create [Edge for the Commit](../definition/commit.md) and add it to the [New Commit](../definition/commit.md).
        * Set [id](../definition/commit.md) to the [Edge's ID](../definition/element-id.md).
        * Set [label](../definition/commit.md) to the [Edge's Label](../definition/element-label.md).
        * Set [from](../definition/commit.md) to the [Edge's From Node ID](../definition/edge.md).
        * Set [to](../definition/commit.md) to the [Edge's To Node ID](../definition/edge.md).
        * Set [action](../definition/commit-action.md) to `update`.
        * Set [props](../definition/commit.md) to the [Commit's Edge's Properties](../definition/commit.md).
        * Set [origProps](../definition/commit.md) to the [Edge's Properties](../definition/element-properties.md).
    1. Else create [Edge for the Commit](../definition/commit.md) and add it to the [New Commit](../definition/commit.md).
        * Set [id](../definition/commit.md) to the [Commit's Edge's ID](../definition/commit.md).
        * Set [label](../definition/commit.md) to the [Commit's Edge's Label](../definition/commit.md).
        * Set [from](../definition/commit.md) to the [Commit's Edge's From](../definition/commit.md).
        * Set [to](../definition/commit.md) to the [Commit's Edge's To](../definition/commit.md).
        * Set [action](../definition/commit-action.md) to `create`.
        * Set [props](../definition/commit.md) to the [Commit's Edge's Properties](../definition/commit.md).
1. For each [Commit's Edge](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `delete`:
    1. If [Edge](../definition/edge.md) is present in the graph, create [Edge for the Commit](../definition/commit.md) and add it to the [New Commit](../definition/commit.md).
        * Set [id](../definition/commit.md) to the [Edge's ID](../definition/element-id.md).
        * Set [label](../definition/commit.md) to the [Edge's Label](../definition/element-label.md).
        * Set [from](../definition/commit.md) to the [Edge's From Node ID](../definition/edge.md).
        * Set [to](../definition/commit.md) to the [Edge's To Node ID](../definition/edge.md).
        * Set [action](../definition/commit-action.md) to `delete`.
        * Set [origProps](../definition/commit.md) to the [Edge's Properties](../definition/element-properties.md).
    1. Else continue.
1. For each [Commit's Node](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `create` or `update` and [Commit's Node](../definition/commit.md) is NOT a [Boundary](../definition/commit-boundary.md):
    1. If [Node](../definition/node.md) is present in the graph and is NOT a [Boundary](../definition/boundary-node.md), create [Node for the Commit](../definition/commit.md) and add it to the [New Commit](../definition/commit.md).
        * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
        * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
        * Set [action](../definition/commit-action.md) to `update`.
        * Set [boundary](../definition/commit-boundary.md) to `false`.
        * Set [props](../definition/commit.md) to the [Commit's Node's Properties](../definition/commit.md).
        * Set [origProps](../definition/commit.md) to the [Node's Properties](../definition/element-properties.md).
    1. Else if [Node](../definition/node.md) is present in the graph and is a [Boundary](../definition/boundary-node.md), create [Node for the Commit](../definition/commit.md) and add it to the [New Commit](../definition/commit.md).
        * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
        * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
        * Set [action](../definition/commit-action.md) to `update`.
        * Set [boundary](../definition/commit-boundary.md) to `false`.
        * Set [props](../definition/commit.md) to the [Commit's Node's Properties](../definition/commit.md).
        * Set [origRepo](../definition/commit.md) to the [Node's Repo](../definition/node-repo.md).
    1. Else [Node](../definition/node.md) is NOT present in the graph, create [Node for the Commit](../definition/commit.md) and add it to the [New Commit](../definition/commit.md).
        * Set [id](../definition/commit.md) to the [Commit's Node's ID](../definition/commit.md).
        * Set [label](../definition/commit.md) to the [Commit's Node's Label](../definition/commit.md).
        * Set [action](../definition/commit-action.md) to `create`.
        * Set [boundary](../definition/commit-boundary.md) to `false`.
        * Set [props](../definition/commit.md) to the [Commit's Node's Properties](../definition/commit.md).
1. For each [Commit's Node](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `delete` and [Commit's Node](../definition/commit.md) is NOT a [Boundary](../definition/commit-boundary.md):
    1. If [Node](../definition/node.md) is present in the graph and is NOT a [Boundary](../definition/boundary-node.md), create [Node for the Commit](../definition/commit.md) and add it to the [New Commit](../definition/commit.md).
        * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
        * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
        * Set [action](../definition/commit-action.md) to `delete`.
        * Set [boundary](../definition/commit-boundary.md) to `false`.
        * Set [origProps](../definition/commit.md) to the [Node's Properties](../definition/element-properties.md).
    1. Else if [Node](../definition/node.md) is present in the graph and is a [Boundary](../definition/boundary-node.md), create [Node for the Commit](../definition/commit.md) and add it to the [New Commit](../definition/commit.md).
        * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
        * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
        * Set [action](../definition/commit-action.md) to `delete`.
        * Set [boundary](../definition/commit-boundary.md) to `true`.
        * Set [origRepo](../definition/commit.md) to the [Node's Repo](../definition/node-repo.md).
    1. Else [Node](../definition/node.md) is NOT present in the graph, continue.
1. For each [Commit's Node](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `create` or `update` and [Commit's Node](../definition/commit.md) is a [Boundary](../definition/commit-boundary.md):
    1. If [Node](../definition/node.md) is present in the graph and is NOT a [Boundary](../definition/boundary-node.md), continue.
    1. Else if [Node](../definition/node.md) is present in the graph and is a [Boundary](../definition/boundary-node.md), create [Node for the Commit](../definition/commit.md) and add it to the [New Commit](../definition/commit.md).
        * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
        * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
        * Set [action](../definition/commit-action.md) to `update`.
        * Set [boundary](../definition/commit-boundary.md) to `true`.
        * Set [repo](../definition/commit.md) to the [Commit's Node's Repo](../definition/commit.md).
        * Set [origRepo](../definition/commit.md) to the [Node's Repo](../definition/node-repo.md).
    1. Else [Node](../definition/node.md) is NOT present in the graph, create [Node for the Commit](../definition/commit.md) and add it to the [New Commit](../definition/commit.md).
        * Set [id](../definition/commit.md) to the [Commit's Node's ID](../definition/commit.md).
        * Set [label](../definition/commit.md) to the [Commit's Node's Label](../definition/commit.md).
        * Set [action](../definition/commit-action.md) to `create`.
        * Set [boundary](../definition/commit-boundary.md) to `true`.
        * Set [repo](../definition/commit.md) to the [Commit's Node's Repo](../definition/commit.md).
1. For each [Commit's Node](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `delete` and [Commit's Node](../definition/commit.md) is a [Boundary](../definition/commit-boundary.md):
    1. If [Node](../definition/node.md) is present in the graph and is a [Boundary](../definition/boundary-node.md), create [Node for the Commit](../definition/commit.md) and add it to the [New Commit](../definition/commit.md).
        * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
        * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
        * Set [action](../definition/commit-action.md) to `delete`.
        * Set [boundary](../definition/commit-boundary.md) to `true`.
        * Set [origRepo](../definition/commit.md) to the [Node's Repo](../definition/node-repo.md).
    1. Else [Node](../definition/node.md) is NOT a [Boundary](../definition/boundary-node.md) or NOT present in the graph, continue.
1. For each [Commit's Node](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `reference` and [Commit's Node's ID](../definition/element-id.md) is in `References To Create`:
    1. If [Node](../definition/node.md) is present in the graph, continue.
    1. Else create [Node for the Commit](../definition/commit.md) and add it to the [New Commit](../definition/commit.md).
        * Set [id](../definition/commit.md) to the [Node's ID](../definition/element-id.md).
        * Set [label](../definition/commit.md) to the [Node's Label](../definition/element-label.md).
        * Set [action](../definition/commit-action.md) to `create`.
        * Set [boundary](../definition/commit-boundary.md) to `true`.
        * Set [repo](../definition/commit.md) to the [Commit's Node's Repo](../definition/commit.md).
1. Return the [New Commit](../definition/commit.md).

## Returns

The [Commit](../definition/commit.md).

## Notes

**Edges**

|                 | Edge Present | Edge Absent |
| :-------------: | :----------: | :---------: |
| **Create Edge** | Update       | Create      |
| **Update Edge** | Update       | Create      |
| **Delete Edge** | Delete       | Drop        |

**Nodes**

|                           | Node Present | Boundary Present | Node Absent |
| :-----------------------: | :----------: | :--------------: | :---------: |
| **Create Node**           | Update       | Transform (2)    | Create      |
| **Update Node**           | Update       | Transform (2)    | Create      |
| **Delete Node**           | Delete (1)   | Delete (1,3)     | Drop        |
| **Create Boundary Node**  | Drop (4)     | Update           | Create      |
| **Update Boundary Node**  | Drop (4)     | Update           | Create      |
| **Delete Boundary Node**  | Drop (5)     | Delete (1)       | Drop        |
| **Boundary Node -> Node** | Update (6)   | Transform (7)    | Create      |
| **Node -> Boundary Node** | Drop (8)     | Update (9)       | Create      |

1. When deleting Nodes, merge will ensure that any attached Edges are also deleted in the Commit.
2. You are pulling in their changes locally, so transform the Boundary Node into a Node.
3. If someone deleted the Node, delete the Boundary Node pointing at it.
4. If someone creates or updates Boundary Nodes, we maintain our own Nodes.
5. If someone removes a Boundary Node, we still keep our Node.
6. If someone pulls in and adds information to a Node, we update our Node with that information.
7. You want the information they updated, so tramsform the Boundary Node into a Node.
8. If someone starts pointing to another Repo, we still maintain out own Nodes.
9. If someone starts pointing to another Repo, we start pointing to that Repo.