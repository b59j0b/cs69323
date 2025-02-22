java c
Homework 6: Measuring Binary Search Trees and AVL Trees
Overview and Objectives
Organization of Classes and Files
Empirical Testing of Data Structures
                   Sample spreadsheet for your data - make a copy
How to Test
Challenge Bonus Problem!
How to Submit
Overview and Objectives
Homework 6 is similar to Homework 3 and Homework 5, but instead implements   two different kinds of binary search trees. Write the same methods for two different implementations of binary search trees— regular   binary search tree   and   self-balancing   AVL tree—and measure their performance empirically.
Binary search trees satisfy the property that the key of each internal node is greater than all the keys in the respective node's left subtree and less than the ones in its right subtree. This property allows us to use an algorithm similar to binary search for   insert(),   find(), and   remove(). The latter two operations may   cause the tree to become less balanced, resulting in a degradation in performance for   find().
A self-balancing tree can use property preserving rotations of groups of tree nodes to help keep the tree more balanced to ensure the performance of   insert(),   find(), and   remove()   are proportional to lgN, where N   is the number of keys in the binary search tree.
AVL Tree   is one such self-balancing tree, which features two different types of rotation (single or double), each with two variants (left or right).    Red-Black trees   are another, which has 14 different rotations, making it less suitable for implementation in a Homework project.
With each algorithm, it is important to identify what situation might cause the   worst case   execution time. We measure both the worst case execution time observed, the average case, and the best case. But most importantly, we want to understand what situations will cause each of these to occur. Run your program and collect measurements for the input test files:   random.txt   (which are randomly shuffled) and   sorted.txt   (which are sorted into ascending alphabetical order ignoring letter case). Your program should   not   ignore letter   cases, so the words that start with an uppercase letter will all come before any words that start with a lowercase letter.
Again, write many helper functions to do the hard work for the public methods. Not only does this practice keep our functions small and easier to understand/debug, this design allows us to use recursion if we wish to implement shorter and more elegant solutions.
All three operations will have the same time complexity, because they are each proportional to O(h), where h   is the height of the binary search tree. If things go well, h   is proportional to jgN. However, in regular binary search trees, h   can be proportional to N   if the tree is skewed to the left or to the right.    This skewing results from inserting keys that are somewhat sorted (in either ascending or descending order).
Also, it is time to practice more C++! This is an ideal time for another   iterator   and to practice converting a class to be a   template. Write an iterator for   BST, and convert your   BST   hierarchy into a template where the types for both key and value are parameterized.
Organization of Classes and Files
Define a class hierarchy with a base class, named   BST, and two derived classes named   BSTree   and   AVLTree,   with the public methods and the private helper functions provided in   BST.h. Again, define a simple framework for measuring the performance of the methods   insert(),   find(), and   remove(). Your goal is to understand the behaviors of both balanced and unbalanced binary search trees given different ordering of input data (one random and the other sorted).
Keep your functions small and clean, so they are easier to understand, debug, and reuse!! Give each function a good name, descriptive of its purpose, with good parameters also with descriptive names.
Some of the code you wrote in earlier homework assignments is reusable for Homework 6.Code for bst.h and other needed files is provided on the   hw6 repo   on GitHub.
We also need class   TreeNode— a helper class to implement a binary search tree—with three essential data members:    key   of type   std::string, and   left   and   right   of type   TreeNode*.    We also add   value   (of any type) when implementing a   map   (as opposed to a   set), and   int   height   required for the balanced AVL tree.  代 写Homework 6: Measuring Binary Search Trees and AVL TreesC/C++
代做程序编程语言  Use these names, so we are all speaking the same language. Do not add any other data members. Definitely do not add getters/setters.Each   BST   will have one important data member   TreeNode * root, which is the pointer to access our linked tree, similar to how   ListNode * head   is the pointer to access our singly linked list contained within our classes. We add   string name,   and   int count   for better information output by our measurement framework.Data members   root,   count,   name,   class TreeNode, and methods   find(),   print(), and the iterator will be the same for both concrete types of   BSTs. Factor them out and move them up to the   BST   class, so now we need to define them only once, and then they are inherited by the derived classes (BSTree   and   AVLTree).Write a random-access iterator for   BST.    Write it once at the   BST   level, and it will work for both concrete   BST   implementations. Use your iterators to write print methods for each concrete class.    The print method should bevoid print(ostream    out) {for (auto e : *this)out << e << ‘ ‘;}Empirical Testing of Data StructuresIn the same way as with earlier Homework assignments, empirically measure the execution times of the operations   insert(),   find(), and   remove()   for both of our BSTs with   std::string   and with large sample input files derived from the Linux dictionary. The file   random.txt   is a random shuffle of these words, and   sorted.txt   is a sorted list of these same words. Each file has 45,392 words, a reasonably large N. This number is defined as   constexpr   NWORDS   at the top of   bst.h.Using a BST means that we DO care what order the entries are in, so we can define three different traversals: in-order, pre-order, and post-order.    in-order will allow us to visit the nodes in alphabetical order, and you can imagine having different iterators for each type of traversal. However, we will only implement the in-order traversal for our   BST::iterator.Use the same measurement technique as in earlier homework assignments, which divides the data into K partitions, then measures performance of each algorithm (insert(),   find(),   remove()) for each concrete data structure (BSTree   and   AVLTree) and for each input file (random.txt   and   sorted.txt).Sample spreadsheet for your data - make a copy
https://docs.google.com/spreadsheets/d/1KgxZ0s5HgHdImVjgnslmbBg0FlzaOdFbNDi5Jz4-ccg/edit?gid=0#gid=0
How to Test
Write good GTests for class   BST.    Apply them to both concrete implementations of binary search trees. We may provide some GTests on the   GitHub hw6 repo,   but you must practice and reinforce the habit of writing good GTests for your programs each week.Be sure to   print out your lists to verify they are in sorted order   when using an in-order traversal!   Create a   smaller input file for initial testing   until you are convinced your program is working correctly. I created two sample files   shortrandom.txt   and   shortsorted.txt   that I found useful for initial testing and debugging. Once your program seems to be working correctly, run it on the full word file. Try it on both   random.txt   and   sorted.txt   to see how they compare.Mentally trace (execute) every function you write on a simple input test case to strengthen your skill in mental debugging!   You will be amazed how much time it will save you in debugging. As you spend less time debugging and more time creating programs, programming becomes much more enjoyable. Always keep your functions small, and be eager to invent helper functions - even if they are one-liners.    Writing small functions and mental tracing for debugging is the path to enjoying programming!Challenge Bonus Problem!To challenge yourself and get a headstart on preparing for job interviews, solve   this LeetCode   Medium problem.   Always start solving by writing on paper or on a whiteboard. Devise the simple, obvious solution first, then consider how you can make it more efficient using what you know about algorithms and data structures. How can you identify that using a binary search tree leads to a superior solution?How to   SubmitIn   GradeScope   for   Homework   6,   upload from GitHub   these files detailed above:
·   .Analysis_46HW6
·   timer.h
·   bst.h
·   bst.cpp (initially EMPTY)
·   bstree.h
·   bstree.cpp (initially EMPTY)
·   avltree.h
·   avltree.cpp (initially EMPTY)
·   main.cpp
   

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
