# Linked Lists

A linked list is  a linear data structure, in which the elements are not stored at contiguous memory locations. Simply, a linked list consists of nodes where each node contains a data field and a reference(link) to the next node in the list.

![Linkedlist](https://user-images.githubusercontent.com/76460786/156234372-99011874-a5a9-40ff-8a86-6aab81e4e4f7.png)

**Like arrays**, Linked List is a linear data structure. **Unlike arrays**, linked list elements are not stored at a contiguous location; the elements are linked using pointers.

## Why Use a Linked List Over an Array?
1) Dynamic size: The size of an array is fixed
2) Ease of insertion/deletion: Inserting a new element in an array of elements is expensive because the room has to be created for the new element(s). To create room, existing elements have to be shifted, but in Linked list if we have the head node then we can traverse to any node through it and insert new node at the required position.

_Example:_
In a system, if we maintain a sorted list of IDs in an array id[]. 
id[] = [1000, 1010, 1050, 2000, 2040]. 
And if we want to insert a new ID 1005, then to maintain the sorted order, we have to move all the elements after 1000 (excluding 1000). 
Deletion is also expensive with arrays, unless some special techniques are used. For example, to delete 1010 in id[], everything after 1010 has to be moved. Due to this, so much work is being done which affects the efficiency of the code

The first node is called the **head**. If the linked list is empty, then the value of the head points to NULL. 
Each node in a list consists of at least two parts: 
1) data (we can store integer, strings or any type of data).
2) Pointer (Or Reference) to the next node (connects one node to another)

```
class LinkedList {
    Node head; // head of the list
 
    /* Linked list Node*/
    class Node {
        int data;
        Node next;
 
        // Constructor to create a new node
        // Next is by default initialized
        // as null
        Node(int d) { data = d; }
    }
}
```

Let's create a simple linked list with three nodes
```
class LinkedList {
    Node head; // head of list
 
    /* Linked list Node.  This inner class is made static so that
       main() can access it */
    static class Node {
        int data;
        Node next;
        Node(int d)
        {
            data = d;
            next = null;
        } // Constructor
    }
 
    /* method to create a simple linked list with 3 nodes*/
    public static void main(String[] args)
    {
        /* Start with the empty list. */
        LinkedList llist = new LinkedList();
 
        llist.head = new Node(1);
        Node second = new Node(2);
        Node third = new Node(3);
 
        /* Three nodes have been allocated dynamically.
          We have references to these three blocks as head, 
          second and third
 
          llist.head        second              third
             |                |                  |
             |                |                  |
         +----+------+     +----+------+     +----+------+
         | 1  | null |     | 2  | null |     |  3 | null |
         +----+------+     +----+------+     +----+------+ */
 
        llist.head.next = second; // Link first node with the second node
 
        /*  Now next of the first Node refers to the second.  So they
            both are linked.
 
         llist.head        second              third
            |                |                  |
            |                |                  |
        +----+------+     +----+------+     +----+------+
        | 1  |  o-------->| 2  | null |     |  3 | null |
        +----+------+     +----+------+     +----+------+ */
 
        second.next = third; // Link second node with the third node
 
        /*  Now next of the second Node refers to third.  So all three
            nodes are linked.
 
         llist.head        second              third
            |                |                  |
            |                |                  |
        +----+------+     +----+------+     +----+------+
        | 1  |  o-------->| 2  |  o-------->|  3 | null |
        +----+------+     +----+------+     +----+------+ */
    }
}
```

## Linked List Traversal 
```
class LinkedList {
    Node head; // head of list
 
    /* Linked list Node.  This inner class is made static so that
       main() can access it */
    static class Node {
        int data;
        Node next;
        Node(int d)
        {
            this.data = d;
            next = null;
        } // Constructor
    }
 
    /* This function prints contents of linked list starting from head */
    public void printList()
    {
        Node n = head;
        while (n != null) {
            System.out.print(n.data + " ");
            n = n.next;
        }
    }
 
    /* method to create a simple linked list with 3 nodes*/
    public static void main(String[] args)
    {
        /* Start with the empty list. */
        LinkedList llist = new LinkedList();
 
        llist.head = new Node(1);
        Node second = new Node(2);
        Node third = new Node(3);
 
        llist.head.next = second; // Link first node with the second node
        second.next = third; // Link second node with the third node
 
        llist.printList();
    }
}
```

`Output: 1 2 3 `
