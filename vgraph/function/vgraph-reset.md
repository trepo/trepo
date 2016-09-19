# reset()
Remove all uncommitted changes.

## Parameters

`none`

## Actions

1. For each [Edge](../definition/edge.md) where [Status](../definition/element-status.md) is greater than `0` (Changed):
    1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted):
        * Set [Status](../definition/element-status.md) to existing [Status](../definition/element-status.md) minus `4`.
    1. If [Status](../definition/element-status.md) is greater than or equal to `2` (Updated):
        * Set [Properties](../definition/element-properties.md) to [Original Properties](../definition/element-original-properties.md).
        * Remove [Original Properties](../definition/element-original-properties.md).
        * Set [Status](../definition/element-status.md) to existing [Status](../definition/element-status.md) minus `2`.
    1. Finally:
        1. If [Status](../definition/element-status.md) is greater than `0`:
            * Remove [Edge](../definition/edge.md).
        1. Else:
            * Set [Status](../definition/element-status.md) to `0`.

1. For each [Node](../definition/node.md) where [Status](../definition/element-status.md) is greater than `0` (Changed):
    1. If [Status](../definition/element-status.md) is greater than or equal to `4` (Deleted):
        * Set [Status](../definition/element-status.md) to existing [Status](../definition/element-status.md) minus `4`.
    1. If [Status](../definition/element-status.md) is greater than or equal to `2` (Updated):
        1. If [Original Properties](../definition/element-original-properties.md) is set:
            * Set [Properties](../definition/element-properties.md) to [Original Properties](../definition/element-original-properties.md).
            * Remove [Original Properties](../definition/element-original-properties.md).
            * Remove [Repo](../definition/node-repo.md) if set.
        1. Else [Original Repo](../definition/node-original-repo.md) is set:
            * Set [Repo](../definition/node-repo.md) to [Original Repo](../definition/node-original-repo.md).
            * Remove [Original Repo](../definition/node-original-repo.md).
            * Remove [Properties](../definition/element-properties.md) if set.
        1. Finally:
            * Set [Status](../definition/element-status.md) to existing [Status](../definition/element-status.md) minus `2`.
    1. Finally:
        1. If [Status](../definition/element-status.md) is greater than `0`:
            * Remove [Node](../definition/node.md).
        1. Else:
            * Set [Status](../definition/element-status.md) to `0`.

## Returns

`nothing`