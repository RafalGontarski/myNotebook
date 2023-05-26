# ALGORITHM

#### How does Binary Search work?
#### What is “Stack overflow”?
#### What is algorythimc complexity?
#### What is linked list?
#### What is QuickSort? Describe the main logic of this sorting algorithm.
#### What is the difference between Stack and Queue data structure?
#### What kinds of sorting mechanis do you know? What are the differences between them?

#### When would you use LinkedList over an ArrayList?

>LinkedList and ArrayList are two common implementations of the List interface in Java. The main difference between the two is the way they store and access elements.

>An ArrayList is backed by an array, which means that it has a fixed size and inserting or removing elements can be expensive, as the underlying array needs to be resized and elements need to be shifted. However, accessing elements by index is fast, as it can be done in constant time.

>On the other hand, a LinkedList is implemented as a series of nodes that contain the data and a reference to the next node in the list. This means that inserting or removing elements is fast, as it only requires updating a few references. However, accessing elements by index can be slow, as the list needs to be traversed from the beginning until the desired element is found.

>In general, you would use an ArrayList when you need fast access to elements by index and when the number of insertions and removals is small compared to the number of accesses. This is because ArrayList has constant-time access and linear-time insertions/removals.

>You would use a LinkedList when you need fast insertions and removals and when you don't need to access elements by index very often. This is because LinkedList has constant-time insertions/removals and linear-time access.

>In addition, LinkedList can be useful when you need to manipulate a list in a way that requires a lot of element insertions and removals, such as when implementing a queue or a stack. In such cases, LinkedList can be more efficient than ArrayList.