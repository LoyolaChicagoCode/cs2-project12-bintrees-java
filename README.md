# Loyola COMP 271 Lab 10 *(FALL 2018)*

Under construction until further notice.

# Individual project

Collaborate with your classmates on a conceptual level but do not share code.
Submit individually.

# Objectives

An understanding of the following concepts and techniques:

- ADT implementation perspective
- dynamically allocated objects
- binary trees
- nonlinear linked structures
- navigating through binary trees
- iterators
  
# Instructions

In this lab, you will have the opportunity to look "under the hood" of linked lists by creating and manipulating nodes.
You will do this interactively using the JShell that comes with Java 10.

1. Start the JShell like so:

       jshell -R-ea

   If this does not work, double-check your Java 10 installation.

1. Define this generic binary tree node class:

       class BTNode<E> {
         public E data;
         public BTNode<E> left;
         public BTNode<E> right;
         public BTNode(final E data, final BTNode<E> left, final BTNode<E> right) { 
           if (data == null) throw new IllegalArgumentException("data is null");
           this.data = data; 
           this.left = left;
           this.right = right;
         }
         public BTNode(final E data) { this(data, null, null); }
         public String toString() { 
           final StringBuilder result = new StringBuilder();
           result.append("BTNode@");
           result.append(hashCode());
           result.append("(");
           result.append(data);
           result.append(", ");
           result.append(left != null ? "BTNode@" + left.hashCode() : ".");
           result.append(", ");
           result.append(right != null ? "BTNode@" + right.hashCode() : ".");
           result.append(")");
           return result.toString();
         }
       }
       
   Hint: If you make a mistake in a class or method definition, don't worry. 
   You can just reenter it to replace the erroneous or incomplete definition.
   
1. *Question:* In the `toString` method, why are we using `StringBuilder` instead of the `+` operator?

1. Create an empty binary tree, represented as null:

       BTNode<Integer> empty = null

1. Create a leaf:

       BTNode<Integer> leaf = new BTNode<>(9)

1. Create the following binary tree. Use as many statements as you want to build up the tree successively.

             1
           /   \
         2       3
        / \     / \
       4   5   6   7
              /
             8


1. Now create the same tree using a single statement involving nested constructor invocations.

1. *Question:* Which way to create the tree more clearly conveys the actual structure of the tree?

1. Define a method for printing the data values in a tree in the following order ("inorder"): 

   a. print the nodes in the left subtree
   
   b. print the root node
   
   c. print the nodes in the right subtree

   For example, for the tree above, your method should print
   
       4 2 5 1 8 6 3 7

   Be sure to handle special cases correctly, such as empty trees and leaves.

       <E> void printTree(BTNode<E> root) { ... }
  
   Hint: Use recursion as you see fit.
   
1. Now define a method for printing the data values in a tree in the following order ("postorder"):

   b. print the root node
   
   a. print the nodes in the left subtree
   
   c. print the nodes in the right subtree

   For example, for the tree above, your method should print
   
       4 2 5 1 8 6 3 7

   Be sure to handle special cases correctly, such as empty trees and leaves.

       <E> void printTree(BTNode<E> root) { ... }
  
   Hint: Use recursion as you see fit.


# Deliverables and submission

Please submit the following deliverables:

- Individual Sakai submission under "Lab 10":
  - gist with JShell history and written part (see below for details)
  - brief description of your collaboration style and summary of your 
    individual contributions to this team project

# Grading

- 3 JShell history (`jshell> /save -history myhistory.jsh`) showing the steps described above (it's OK if errors are included)
- 1 written part
  - 0.2 for each of the four questions
  - 0.2 grammar and style
- 1 submission of both deliverables as part of a single secret [gist](https://gist.github.com/)
  - go to http://gist.github.com and create a new gist by clicking the corresponding button in the top right corner
  - upload your JShell history by dragging it from your desktop into the gist editor
  - choose add file to open another editor and enter your answers there
  - *finally, submit this gist's URL through Sakai*
  - [GitHub gist documentation](https://help.github.com/articles/creating-gists/)

*5 points TOTAL*

# References

- [JShell overview](https://docs.oracle.com/javase/9/jshell/introduction-jshell.htm)
- [JShell tutorial](http://cr.openjdk.java.net/~rfield/tutorial/JShellTutorial.html)