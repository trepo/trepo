# undo(ID)
Undo all commits back to ID.

## Parameters

* [ID](../definition/commit-id.md) - The commit to roll back to.

## Actions

**Note:** Node creation must come before Edge creation, and Node deletion must come after Edge deletion. So 1) Undo Node delete, 2) Undo Edge delete, 3) Undo Edge update, 4) Undo Edge create, 5) Undo Node update, 6) Undo Node create.

1. If [ID](../definition/commit-id.md) is invalid, [Error](../definition/error.md).
1. If there are uncommitted changes, [Error](../definition/error.md).
1. If there is no [Commit Node](../definition/commit-node.md) identified by [ID](../definition/commit-id.md), [Error](../definition/error.md).
1. For each [Current Commit Node](../definition/commit-node.md) starting at the [Root Node](../definition/root-node.md), following each incoming [Commit Edges](../definition/commit-edge.md) to the previous [Commit Node](../definition/commit-node.md), and ending at the [Commit Node](../definition/commit-node.md) identified by [ID](../definition/commit-id.md):
    1. If [Current Commit Node](../definition/commit-node.md) is the one identified by [ID](../definition/commit-id.md), break;
    1. Create a new [Commit Edge](../definition/commit-edge.md) from the [Current Commit Node's](../definition/commit-node.md) previous (if any) [Commit Node](../definition/commit-node.md) to the [Root Node](../definition/root-node.md). There should be 2 [Commit Edges](../definition/commit-edge.md) going into the [Root Node](../definition/root-node.md) now.
    1. Create [Commit](../definition/commit.md) from the [Current Commit Node](../definition/commit-node.md).
    1. For each [Commit's Node](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `delete`:
        1. If [Commit's Node](../definition/commit.md) is a [Boundary](../definition/commit-boundary.md), create a new [Boundary Node](../definition/boundary-node.md).
            * Set [ID](../definition/element-id.md) to [Commit's Node ID](../definition/commit.md).
            * Set [Label](../definition/element-label.md) to [Commit's Node Label](../definition/commit.md).
            * Set [Repo](../definition/repo.md) to [Commit's Node Repo](../definition/commit.md).
            * Set [Status](../definition/element-status.md) to `0`.
        1. Else create a new [Node](../definition/node.md)
            * Set [ID](../definition/element-id.md) to [Commit's Node ID](../definition/commit.md).
            * Set [Label](../definition/element-label.md) to [Commit's Node Label](../definition/commit.md).
            * Set [Properties](../definition/element-properties.md) to [Commit's Node Original Properties](../definition/commit.md).
            * Set [Status](../definition/element-status.md) to `0`.
    1. For each [Commit's Edge](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `delete`:
        1. Create a new [Edge](../definition/edge.md) from [Commit's Edge From](../definition/commit.md) to [Commit's Edge To](../definition/commit.md).
            * Set [ID](../definition/element-id.md) to [Commit's Edge ID](../definition/commit.md).
            * Set [Label](../definition/element-label.md) to [Commit's Edge Label](../definition/commit.md).
            * Set [Properties](../definition/element-properties.md) to [Commit's Edge Original Properties](../definition/commit.md).
            * Set [Status](../definition/element-status.md) to `0`.
    1. For each [Commit's Edge](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `update`:
        1. Update [Edge](../definition/edge.md):
            * Remove [Properties](../definition/element-properties.md).
            * Set [Properties](../definition/element-properties.md) to [Commit's Edge Original Properties](../definition/commit.md).
    1. For each [Commit's Edge](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `create`:
        1. Remove [Edge](../definition/edge.md) from the graph.
    1. For each [Commit's Node](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `update`:
        1. If [Commit's Node](../definition/commit.md) is a [Boundary](../definition/commit-boundary.md):
            1. If [Commit's Node Original Properties](../definition/commit.md) is set, transform [Boundary Node](../definition/boundary-node.md) back into a [Node](../definition/node.md).
                * Remove [Repo](../definition/node-repo.md).
                * Set [Properties](../definition/element-properties.md) to [Commit's Node Original Properties](../definition/commit.md).
            1. Else update [Boundary Node](../definition/boundary-node.md).
                * Set [Repo](../definition/node-repo.md) to [Commit's Node Original Repo](../definition/commit.md).
        1. Else:
            1. If [Commit's Node Original Repo](../definition/commit.md) is set, transform [Node](../definition/node.md) back into a [Boundary Node](../definition/boundary-node.md).
                * Remove [Properties](../definition/element-properties.md).
                * Set [Repo](../definition/node-repo.md) to [Commit's Node Original Repo](../definition/commit.md).
            1. Else update [Node](../definition/node.md).
                * Remove [Properties](../definition/element-properties.md).
                * Set [Properties](../definition/element-properties.md) to [Commit's Node Original Properties](../definition/commit.md).
    1. For each [Commit's Node](../definition/commit.md) in the [Commit](../definition/commit.md) where the [Action](../definition/commit-action.md) is equal to `create`:
        1. Remove [Node](../definition/node.md) from the graph.
    1. Remove the [Current Commit Node](../definition/commit-node.md). This will also remove the incoming and outgoing [Commit Edges](../definition/commit-edge.md).

## Returns

An Array or List of [Commit IDs](../definition/commit-id.md).

## Notes

**Undoing Commit Edges**

|                 | Commit `action` | Commit `props` | Commit `origProps` | To Do | 
| :-------------: | :-------------: | :------------: | :----------------: | :---: |
| **Undo Create** | `create`        | X              |                    | (1)   |
| **Undo Update** | `update`        | X              | X                  | (2)   |
| **Undo Delete** | `delete`        |                | X                  | (3)   |

1. Delete Edge.
2. Set Edge Properties to `origProps`.
3. Create Edge and Set Edge Properties to `origProps`.

** Undoing Commit Nodes**

|                                | Commit `action` | Commit `boundary` | Commit `repo` | Commit `origRepo` | Node Repo | Commit `props` | Commit `origProps` | Node Properties | To Do | 
| :----------------------------: | :-------------: | :---------------: | :-----------: | :---------------: | :-------: | :------------: | :----------------: | :-------------: | :---: |
| **Undo Create Node**           | `create`        | False             |               |                   |           | X              |                    | Set             | (1)   |
| **Undo Update Node**           | `update`        | False             |               |                   |           | X              | X                  | Set             | (2)   |
| **Undo Delete Node**           | `delete`        | False             |               |                   | N/A       |                | X                  | N/A             | (3)   |
| **Undo Create Boundary Node**  | `create`        | True              | X             |                   | Set       |                |                    |                 | (4)   |
| **Undo Update Boundary Node**  | `update`        | True              | X             | X                 | Set       |                |                    |                 | (5)   |
| **Undo Delete Boundary Node**  | `delete`        | True              |               | X                 | N/A       |                |                    | N/A             | (6)   |
| **Undo Boundary Node -> Node** | `update`        | False             |               | X                 |           | X              |                    | Set             | (7)   |
| **Undo Node -> Boundary Node** | `update`        | True              | X             |                   | Set       |                | X                  |                 | (8)   |

1. Delete Node.
2. Set Node Properties to `origProps`.
3. Create Node and Set Node Properties to `origProps`.
4. Delete Node ONLY IF Node Repo is set and equal to Commit `origRepo`.
5. Set Node Repo to `origRepo`.
6. Delete Node.
7. Set Node Repo to `origRepo` and remove Node Properties.
8. Set Node Properties to `origProps` and remove Node Repo.