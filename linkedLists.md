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

## Inserting a Node
A node can be added in three different ways in a linked list...
1) At the front of the linked list 
2) After a given node. 
3) At the end of the linked list.

**Adding a Node to the Front:** 
_Example:_ If the given Linked List is 10->15->20->25 and we add an item 5 at the front, then the Linked List becomes 5->10->15->20->25. The newly added node, 5, becomes the new head.

```
public void push(int new_data)
{
    /* 1 & 2: Allocate the Node &
              Put in the data*/
    Node new_node = new Node(new_data);
 
    /* 3. Make next of new Node as head */
    new_node.next = head;
 
    /* 4. Move the head to point to new Node */
    head = new_node;
}
```
`Time complexity of push() is O(1)` as it does a constant amount of work.

**Adding a Node After a Given Node** 
We are given a pointer to a node, and the new node is inserted after the given node.

```
public void insertAfter(Node prev_node, int new_data)
{
    /* 1. Check if the given Node is null */
    if (prev_node == null) {
        System.out.println(
            "The given previous node cannot be null");
        return;
    }
 
    /* 2. Allocate the Node &
    3. Put in the data*/
    Node new_node = new Node(new_data);
 
    /* 4. Make next of new Node as next of prev_node */
    new_node.next = prev_node.next;
 
    /* 5. make next of prev_node as new_node */
    prev_node.next = new_node;
}
```
`Time complexity of insertAfter() is O(1)`

**Adding a Node at the End**
```
public void append(int new_data)
{
    /* 1. Allocate the Node &
       2. Put in the data
       3. Set next as null */
    Node new_node = new Node(new_data);
 
    /* 4. If the Linked List is empty, then make the
           new node as head */
    if (head == null)
    {
        head = new Node(new_data);
        return;
    }
 
    /* 4. This new node is going to be the last node, so
         make next of it as null */
    new_node.next = null;
 
    /* 5. Else traverse till the last node */
    Node last = head;
    while (last.next != null)
        last = last.next;
 
    /* 6. Change the next of last node */
     last.next = new_node;
    return;
}
```
`Time complexity: 0(n)`

**A complete working Java program to demonstrate all insertion methods on linked list**
```
class LinkedList
{
	Node head; // head of list

	/* Linked list Node*/
	class Node
	{
		int data;
		Node next;
		Node(int d) {data = d; next = null; }
	}

	/* Inserts a new Node at front of the list. */
	public void push(int new_data)
	{
		/* 1 & 2: Allocate the Node &
				Put in the data*/
		Node new_node = new Node(new_data);

		/* 3. Make next of new Node as head */
		new_node.next = head;

		/* 4. Move the head to point to new Node */
		head = new_node;
	}

	/* Inserts a new node after the given prev_node. */
	public void insertAfter(Node prev_node, int new_data)
	{
		/* 1. Check if the given Node is null */
		if (prev_node == null)
		{
			System.out.println("The given previous node cannot be null");
			return;
		}

		/* 2 & 3: Allocate the Node &
				Put in the data*/
		Node new_node = new Node(new_data);

		/* 4. Make next of new Node as next of prev_node */
		new_node.next = prev_node.next;

		/* 5. make next of prev_node as new_node */
		prev_node.next = new_node;
	}
	
	/* Appends a new node at the end. This method is
	defined inside LinkedList class shown above */
	public void append(int new_data)
	{
		/* 1. Allocate the Node &
		2. Put in the data
		3. Set next as null */
		Node new_node = new Node(new_data);

		/* 4. If the Linked List is empty, then make the
			new node as head */
		if (head == null)
		{
			head = new Node(new_data);
			return;
		}

		/* 4. This new node is going to be the last node, so
			make next of it as null */
		new_node.next = null;

		/* 5. Else traverse till the last node */
		Node last = head;
		while (last.next != null)
			last = last.next;

		/* 6. Change the next of last node */
		last.next = new_node;
		return;
	}

	/* This function prints contents of linked list starting from
		the given node */
	public void printList()
	{
		Node tnode = head;
		while (tnode != null)
		{
			System.out.print(tnode.data+" ");
			tnode = tnode.next;
		}
	}

	/* Driver program to test above functions. Ideally this function
	should be in a separate user class. It is kept here to keep
	code compact */
	public static void main(String[] args)
	{
		/* Start with the empty list */
		LinkedList llist = new LinkedList();

		// Insert 6. So linked list becomes 6->NUllist
		llist.append(6);

		// Insert 7 at the beginning. So linked list becomes
		// 7->6->NUllist
		llist.push(7);

		// Insert 1 at the beginning. So linked list becomes
		// 1->7->6->NUllist
		llist.push(1);

		// Insert 4 at the end. So linked list becomes
		// 1->7->6->4->NUllist
		llist.append(4);

		// Insert 8, after 7. So linked list becomes
		// 1->7->8->6->4->NUllist
		llist.insertAfter(llist.head.next, 8);

		System.out.println("\nCreated Linked list is: ");
		llist.printList();
	}
}
```
`Output = 1 7 8 6 4`

