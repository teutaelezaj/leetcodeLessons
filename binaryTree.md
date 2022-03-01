# Binary Tree

A binary tree is a recursive data structure where each node can have 2 children at most. 

## Building the Binary Tree

Step 1: Build the Node class that will store int values, and keep a reference to each child:

```
class Node {
    int value;
    Node left;
    Node right;

    Node(int value) {
        this.value = value;
        right = null;
        left = null;
    }
}
```

Step 2: Add the starting node of our tree (the root):

```
public class BinaryTree {

    Node root;

    // ...
}
```

Step 3: Determine which operations you will use

1) Inserting Elements
  First, we have to find the place where we want to add a new node in order to keep the tree sorted. We'll follow these rules starting from the root node:
> if the new node's value is lower than the current node's, we go to the left child
> if the new node's value is greater than the current node's, we go to the right child
> when the current node is null, we've reached a leaf node and we can insert the new node in that position


Then we'll create a recursive method to do the insertion:
```
private Node addRecursive(Node current, int value) {
    if (current == null) {
        return new Node(value);
    }

    if (value < current.value) {
        current.left = addRecursive(current.left, value);
    } else if (value > current.value) {
        current.right = addRecursive(current.right, value);
    } else {
        // value already exists
        return current;
    }

    return current;
}
```

Next we'll create the public method that starts the recursion from the root node:

```
public void add(int value) {
    root = addRecursive(root, value);
}
```

Let's see how we can use this method to create the tree from our example:

```
private BinaryTree createBinaryTree() {
    BinaryTree bt = new BinaryTree();

    bt.add(6);
    bt.add(4);
    bt.add(8);
    bt.add(3);
    bt.add(5);
    bt.add(7);
    bt.add(9);

    return bt;
}
```

2) Finding an Element: add a method to check if the tree contains a specific value.

```

