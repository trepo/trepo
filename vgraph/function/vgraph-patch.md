# patch(Commit)
Apply the Commit to the graph.

## Parameters

* [Commit](../definition/commit.md) - The commit to apply.

## Actions

**Note:** Node creation must come before Edge creation, and Node deletion must come after Edge deletion. So 1) Node create, 2) Node update, 3) Edge create, 4) Edge update, 5) Edge delete, 6) Node delete.

1. If [Commit](../definition/commit.md) is invalid, [Error](../definition/error.md).
1. If there are uncommitted changes, [Error](../definition/error.md).
1. If [Commit's prev](../definition/commit-prev.md) does not match the latest [Commit Node's ID](../definition/commit-node.md), [Error](../definition/error.md).
1. If there is more than one [Commit Edge](../definition/commit-edge.md) coming into the [Root Node](../definition/root-node.md), [Error](../definition/error.md).
1. Create a [Commit Node](../definition/commit-node.md) with the information in Commit.
1. Create a [Commit Edge](../definition/commit-edge.md) from the latest [Commit Node](../definition/commit-node.md) (or the [Root Node](../definition/root-node.md) if this is the first commit) to the new [Commit Node](../definition/commit-node.md).
1. Create a [Commit Edge](commit_edge.md) from the new Commit Node to the [Root Node](../definition/root-node.md).
1. For each [Commit's Node](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `create`:
    1. If [Node](../definition/node.md) is present in the graph, [Error](../definition/error.md).
    1. If [Commit's Node](../definition/commit.md) is a [Boundary](../definition/commit-boundary.md), create a new [Boundary Node](../definition/boundary-node.md).
        * Set [ID](../definition/element-id.md) to [Commit's Node ID](../definition/commit.md).
        * Set [Label](../definition/element-label.md) to [Commit's Node Label](../definition/commit.md).
        * Set [Repo](../definition/repo.md) to [Commit's Node Repo](../definition/commit.md).
        * Set [Status](../definition/element-status.md) to `0`.
    1. Else create a new [Node](../definition/node.md)
        * Set [ID](../definition/element-id.md) to [Commit's Node ID](../definition/commit.md).
        * Set [Label](../definition/element-label.md) to [Commit's Node Label](../definition/commit.md).
        * Set [Properties](../definition/element-properties.md) to [Commit's Node Properties](../definition/commit.md).
        * Set [Status](../definition/element-status.md) to `0`.
1. For each [Commit's Node](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `update`:
    1. If [Node](../definition/node.md) is NOT present in the graph, [Error](../definition/error.md).
    1. If [Node Label](../definition/element-label.md) does NOT equal [Commit's Node Label](../definition/commit.md), [Error](../definition/error.md).
    1. If [Commit's Node](../definition/commit.md) is a [Boundary](../definition/commit-boundary.md):
        1. If [Node](../definition/node.md) is a [Boundary Node](../definition/boundary-node.md), update it:
            * Set [Repo](../definition/repo.md) to [Commit's Node Repo](../definition/commit.md).
            * Set [Status](../definition/element-status.md) to `0`.
        1. Else downgrade [Node](../definition/node.md):
            * Set [Repo](../definition/repo.md) to [Commit's Node Repo](../definition/commit.md).
            * Remove [Properties](../definition/element-properties.md).
            * Set [Status](../definition/element-status.md) to `0`.
    1. Else:
        1. If [Node](../definition/node.md) is a [Boundary Node](../definition/boundary-node.md), upgrade it:
            * Remove [Repo](../definition/repo.md).
            * Set [Properties](../definition/element-properties.md) to [Commit's Node Properties](../definition/commit.md).
            * Set [Status](../definition/element-status.md) to `0`.
        1. Else update [Node](../definition/node.md):
            * Remove [Properties](../definition/element-properties.md).
            * Set [Properties](../definition/element-properties.md) to [Commit's Node Properties](../definition/commit.md).
            * Set [Status](../definition/element-status.md) to `0`.
1. For each [Commit's Edge](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `create`:
    1. If [Edge](../definition/edge.md) is present in the graph, [Error](../definition/error.md).
    1. If [Commit's Edge From](../definition/commit.md) is NOT present in the graph, [Error](../definition/error.md).
    1. If [Commit's Edge To](../definition/commit.md) is NOT present in the graph, [Error](../definition/error.md).
    1. Create a new [Edge](../definition/edge.md) from [Commit's Edge From](../definition/commit.md) to [Commit's Edge To](../definition/commit.md).
        * Set [ID](../definition/element-id.md) to [Commit's Edge ID](../definition/commit.md).
        * Set [Label](../definition/element-label.md) to [Commit's Edge Label](../definition/commit.md).
        * Set [Properties](../definition/element-properties.md) to [Commit's Edge Properties](../definition/commit.md).
        * Set [Status](../definition/element-status.md) to `0`.
1. For each [Commit's Edge](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `update`:
    1. If [Edge](../definition/edge.md) is NOT present in the graph, [Error](../definition/error.md).
    1. If [Edge Label](../definition/element-label.md) does NOT equal [Commit's Edge Label](../definition/commit.md), [Error](../definition/error.md).
    1. If [Edge From](../definition/edge.md) does NOT equal [Commit's Edge From](../definition/commit.md), [Error](../definition/error.md).
    1. If [Edge To](../definition/edge.md) does NOT equal [Commit's Edge To](../definition/commit.md), [Error](../definition/error.md).
    1. Update [Edge](../definition/edge.md):
        * Remove [Properties](../definition/element-properties.md).
        * Set [Properties](../definition/element-properties.md) to [Commit's Edge Properties](../definition/commit.md).
        * Set [Status](../definition/element-status.md) to `0`.
1. For each [Commit's Edge](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `delete`:
    1. If [Edge](../definition/edge.md) is NOT present in the graph, [Error](../definition/error.md).
    1. If [Edge Label](../definition/element-label.md) does NOT equal [Commit's Edge Label](../definition/commit.md), [Error](../definition/error.md).
    1. If [Edge From](../definition/edge.md) does NOT equal [Commit's Edge From](../definition/commit.md), [Error](../definition/error.md).
    1. If [Edge To](../definition/edge.md) does NOT equal [Commit's Edge To](../definition/commit.md), [Error](../definition/error.md).
    1. Delete [Edge](../definition/edge.md) from the graph.
1. For each [Commit's Node](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `delete`:
    1. If [Node](../definition/node.md) is NOT present in the graph, [Error](../definition/error.md).
    1. If [Node Label](../definition/element-label.md) does NOT equal [Commit's Node Label](../definition/commit.md), [Error](../definition/error.md).
    1. If [Commit's Node](../definition/commit.md) is a [Boundary](../definition/commit-boundary.md):
        1. If [Node](../definition/node.md) is NOT a [Boundary](../definition/boundary-node.md), [Error](../definition/error.md).
        1. Delete [Node](../definition/node.md) from the graph.
    1. Else:
        1. If [Node](../definition/node.md) is a [Boundary](../definition/boundary-node.md), [Error](../definition/error.md).
        1. Delete [Node](../definition/node.md) from the graph.
1. If there is an earlier [Commit Node](../definition/commit-node.md), remove the [Commit Edge](../definition/commit-edge.md) that was pointing from that [Commit Node](../definition/commit-node.md) to the [Root Node](../definition/root-node.md).


## Returns

`none`

## Notes

**Applying Commit Edges**

|            | Edge Present | Edge Absent |
| :--------: | :----------: | :---------: |
| **Create** | Error        | Create      |
| **Update** | Update       | Error       |
| **Delete** | Delete       | Error       |

**Applying Commit Nodes**

|            | Node Present | Boundary Present | Node Absent |
| :--------: | :----------: | :--------------: | :---------: |
| **Create** | Error        | Error (1)        | Create      |
| **Update** | Update       | Upgrade (2)      | Error       |
| **Delete** | Delete       | Error (3)        | Error       |

1. Something must have gone terribly wrong if we had a boundary node before the node we were pointing to existed.
2. This provides the means to bring a Node into our instance if we had a boundary node previously pointing to it. Can only be accomplished via `patch()`.
3. Trying to delete a Node should NOT blindly delete a boundary instead. Something must have gone wrong.

**Applying Commit Boundary Nodes**

|            | Node Present | Boundary Present | Node Absent |
| :--------: | :----------: | :--------------: | :---------: |
| **Create** | Ignore (1)   | Ignore (1)       | Create      |
| **Update** | Update (4)   | Downgrade (3)    | Error       |
| **Delete** | Error (2)    | Delete           | Error       |

1. Because an Edge with Action = `create` or `update` in a Commit must have from and to as Boundary Nodes, applying that patch must ignore trying to re-create those boundary nodes.
2. A Boundary Node with Action = `delete` in a Commit will only delete a Boundary Node, and NOT a regular Node.
3. This provides a way to "kick out" a node and turn it into a boundary. Can be done via `patch()` or `vGraph.setRepo()`.
4. This allows us to update where the repo points to.
