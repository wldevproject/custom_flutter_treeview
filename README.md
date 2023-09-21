# Cloning and Modification from flutter_simple_treeview
This widget visualises a tree structure, where a node can be any widget.

## Demo

[https://flutter_simple_treeview.surge.sh/](https://flutter_simple_treeview.surge.sh/)

## Usage

```
                  TreeView(nodes: [
                    TreeNode(content: Text("root1")),
                    TreeNode(
                      content: Text("root2"),
                      children: [
                        TreeNode(content: Text("child21")),
                        TreeNode(content: Text("child22")),
                        TreeNode(
                          content: Text("root23"),
                          children: [
                            TreeNode(content: Text("child231")),
                          ],
                        ),
                      ],
                    ),
                  ]),
```

## Implementation

```
  custom_flutter_treeview:
    git:
      url: https://github.com/wldevproject/custom_flutter_treeview.git
      ref: main # branch name
```

## default collapse with (allNodesExpanded: false)

```
final TreeController treeController = TreeController(allNodesExpanded: false);
```

## With GetX

```
Widget buildTree(controller, treeController) {
  try {
    return Obx(() {
      controller.isExpandedNetwork == true
          ? treeController.expandAll()
          : treeController.collapseAll();
      return TreeView(
        nodes: toTreeNodes(controller.detailUser.value.downlines),
        treeController: treeController,
      );
    });
  } on FormatException catch (e) {
    return Text(e.message);
  }
}

..
nodes: toTreeNodes(controller.detailUser.value.downlines), -> list generate
..
```
