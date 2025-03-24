### Binary Trees

- Each node has at most two children, referred to as the left and right children.

```c
struct node
{
 int data;
 struct node *left;
 struct node *right;
};
```

---

### 1. Complete Binary Tree

A complete binary tree is just like a full binary tree, but with two major differences

![Screenshot 2025-03-24 at 22 32 49](https://github.com/user-attachments/assets/5faec65a-ac4d-4111-b7e7-0757edfb1570)


### Properties:
- Every level must be completely filled
- All the leaf elements must lean towards the left.
- The last leaf element might not have a right sibling i.e. a complete binary tree doesn't have to be a full binary tree.

---

### 2. Balanced Binary Tree
![Screenshot 2025-03-24 at 22 34 53](https://github.com/user-attachments/assets/2f9b72ee-68e4-4dd9-81ee-d42f200208c9)

A balanced binary tree, also referred to as a height-balanced binary tree, is defined as a binary tree in which the height of the left and right subtree of any node differ by not more than 1.

### Properties:

- difference between the left and the right subtree for any node is not more than one
- the left subtree is balanced
- the right subtree is balanced

