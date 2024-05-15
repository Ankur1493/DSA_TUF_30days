# Intro 
A binary tree is a non-linear data structure in which each node has at most two children, referred to as the left child and the right child.

## Basic Terms 

**Node** 
A node in a binary tree is a fundamental unit that contains a value and has references to its left and right children.

**Parent Node**
A parent node in a binary tree is the node that has a reference to the current node as one of its children

**Child Node**
A child node in a binary tree is a node that is directly connected to another node, referred to as its parent, and is one level below the parent node. Each parent node can have up to two children: a left child and a right child

**Leaf Node**
A node which 0 children

**Root Node**
A node which is the starting point of a tree


## Creation of a Binary tree

```

#include <iostream>
using namespace std;

class node {
public: 
    int data;
    node* left;
    node* right;
    node(int d) {
        this->data = d;
        this->left = NULL;
        this->right = NULL;
    }
};

node* buildTree(node* root) {
    cout << "Enter the data: " << endl;
    int data;
    cin >> data;
    root = new node(data);
    
    if(data == -1) {
        return NULL;
    }
    
    cout << "Enter data for left child: "<< data << endl;
    root->left = buildTree(root->left);
    cout << "Enter data for right child: "<< data << endl;
    root->right = buildTree(root->right);
    
    return root;
}

int main() {
    node* root = NULL;
    root = buildTree(root);
    return 0;
}
```

## Level Order Traversal
Level order traversal is a method of traversing a binary tree where nodes are visited level by level from left to right. This means that all nodes at each level are visited before moving to the next level. This traversal is typically implemented using a queue data structure.

