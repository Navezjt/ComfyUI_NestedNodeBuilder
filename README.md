# ComfyUI_NestedNodeBuilder
Adds a feature that allows for nesting of other nodes for better organization and simplification of repetitive patterns in workflows.

## Disclaimer
This is a prototype and will likely have many problems. This will probably be obsolete once [subgraphs](https://github.com/comfyanonymous/ComfyUI/pull/724) are implemented within ComfyUI. If you do decide to use this, make sure to save your workflow before nesting any nodes just in case. The way nested nodes are saved are subject to change and may become unusable in later commits.

## Installation
Enter the following command from the commandline starting in ComfyUI/custom_nodes/
```
git clone https://github.com/ssitu/ComfyUI_ComfyUI_NestedNodeBuilder
```

## Problems
- Special nodes such as primitive and reroute nodes cannot be nested.
- Nesting two nodes that have a "control_after_generate" widget will cause the resulting node to keep only one of the widgets, and also corrupts the values of widgets that follow it.
- The green outline that indicates which node is being executed is not shown for nested nodes.
- Nested nodes cannot be nested.