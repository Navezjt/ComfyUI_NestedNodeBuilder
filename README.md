# ComfyUI_NestedNodeBuilder
Adds a feature for the default interface in [ComfyUI](https://github.com/comfyanonymous/ComfyUI) that allows for nesting of other nodes for better organization and simplification of repetitive patterns in workflows.

## Disclaimer
This is a prototype and will likely have many problems. This will probably be obsolete once [subgraphs](https://github.com/comfyanonymous/ComfyUI/pull/724) are implemented within ComfyUI. To be safe, save your workflow before nesting any nodes. How nested nodes are saved are subject to change and saved nodes may become unusable in the future.

## Installation
Enter the following command from the commandline starting in ComfyUI/custom_nodes/
```
git clone https://github.com/ssitu/ComfyUI_NestedNodeBuilder
```

## Usage

### Demo:
![NestedNodeBuilderDemo](https://github.com/ssitu/ComfyUI_NestedNodeBuilder/assets/57548627/f88fc1dc-ec64-4a48-b989-2857de088b67)

<details>
  <summary><h3>1. Selecting the nodes to nest</h3></summary>
  Select multiple nodes by using <code>Ctrl/Shift + left/right click</code> on the desired nodes to nest. 
  You can also use <code>Ctrl + left click + drag</code> to highlight nodes.
</details>
<details>
  <summary><h3>2. Nesting the selected nodes</h3></summary>
  After making a selection, <code>right click</code> on any of the selected nodes and select <code>Nest Selected Nodes</code> and choose a name that won't conflict with any other existing node. The selected nodes will be replaced with a new node that contains the selected nodes. You can also unnest the new node by right clicking on the node and clicking <code>Unnest</code>. The selected nodes may also be converted to an already existing nested node using the <code>Convert selected to Nested Node: &ltname&gt</code> option that appears if the selected nodes have a similar structure.
</details>
<details>
    <summary><h3>3. Creating a nested node from the node menu</h3></summary>
    Nested nodes are saved and can be created again from the node menu that appears when you <code>right click</code> on the canvas under the <code>Nested Nodes</code> category.
</details>
<details>
    <summary><h3>4. Where are nested nodes saved?</h3></summary>
    You can find them under <code>ComfyUI/custom_nodes/ComfyUI_NestedNodeBuilder/nested_nodes/</code>. This directory can be changed by editing the <code>nested_nodes_path</code> entry in the <code>config.yaml</code>. The nested nodes are stored as .json files. The names of the nested nodes may be changed by editing their .json files. The changes made to the directory are registered after refreshing the web UI.
</details>

<details>
  <summary><h2>How it works</h2></summary>
  The nodes that are nested are stored in the properties of the nested node. Before the prompt is calculated, the nested node is replaced with the nodes that it stored. After the prompt is calculated, the nodes are nested again. Depending on performance, this may cause a quick flash of what the workflow looks like after the nodes are unnested when queueing a prompt. This seemed to be the approach that was the least intrusive on the ComfyUI codebase.
</details>

## Problems
- Special nodes such as primitive and reroute nodes cannot be nested.
- Nesting two nodes that have a "control_after_generate" widget will cause the resulting node to keep only one of the widgets, and also corrupts the values of widgets that follow it.
- Nested nodes cannot be nested.
- Can't really nest output nodes such as preview image and save image nodes. It works but it won't display the image. You can still see the image if loading the prompt from the history.

## Credits
Inspired by [this repo by Itdrdata](https://github.com/ltdrdata/ComfyUI-Workflow-Component), check it out if you want something more robust and flexible.
