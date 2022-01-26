## [ArrayLists](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html)
```java
import java.util.ArrayList;
ArrayList<Integer> list = new ArrayList<Integer>(); // declare the dynamic array
list.add(2); // [2]
list.add(3); // [2, 3]
list.add(7); // [2, 3, 7]
list.add(5); // [2, 3, 7, 5]
list.set(1, 4); // sets element at index 1 to 4 -> [2, 4, 7, 5]
list.remove(1); // removes element at index 1 -> [2, 7, 5]
// this remove method is O(n); to be avoided
list.add(8); // [2, 7, 5, 8]
list.remove(list.size()-1); // [2, 7, 5]
// here, we remove the element from the end of the list; this is O(1).
System.out.println(list.get(2)); // 5
```
## [Stacks](https://docs.oracle.com/javase/8/docs/api/java/util/Stack.html)
**Last In, First Out (LIFO)</br>
  A stack is a Last In First Out (LIFO) data structure that supports three operations:
```push```, which adds an element to the top of the stack, ```pop```, which removes an element from
the top of the stack, and ```peek```, which retrieves the element at the top without removing it,
all in O(1) time. Think of it like a real-world stack of papers.**
```java
import java.util.Stack;
Stack<Integer> s = new Stack<Integer>();
s.push(1); // [1]
s.push(13); // [1, 13]
System.out.println(s.size()); // 2
s.pop(); // [1]
System.out.println(s.peek()); // 1
s.pop(); // []
System.out.println(s.size()); // 0
```
## [Queues](https://docs.oracle.com/javase/8/docs/api/java/util/Queue.html)
**First In, First Out (FIFO)</br>
A queue is a First In First Out (FIFO) data structure that supports three operations of
```add```, insertion at the back of the queue, ```poll```, deletion from the front of the queue, and ```peek```,
which retrieves the element at the front without removing it, all in O(1) time. Java doesn’t
actually have a Queue class; it’s only an interface. The most commonly used implementation
is the LinkedList, declared as follows: ```Queue q = new LinkedList();```.**
```java
Queue<Integer> q = new LinkedList<Integer>();
q.add(1); // [1]
q.add(3); // [3, 1]
q.poll(); // [3]
q.add(4); // [4, 3]
System.out.println(q.size()); // 2
System.out.println(q.peek()); // 3
```
## [Deques](https://docs.oracle.com/javase/8/docs/api/java/util/Deque.html)
**A deque (usually pronounced “deck”) stands for double ended queue and is a combination
of a stack and a queue, in that it supports O(1) insertions and deletions from both the
front and the back of the deque. In Java, the deque class is called ArrayDeque. The four
methods for adding and removing are ```addFirst```, ```removeFirst```, ```addLast```, and ```removeLast```.
The methods for retrieving the first and last elements without removing are ```peekFirst``` and
```peekLast```.**
```java
ArrayDeque<Integer> deque = new ArrayDeque<Integer>();
deque.addFirst(1); // [1]
deque.addLast(2); // [1, 2]
deque.addFirst(3); // [3, 1, 2]
deque.addFirst(4); // [3, 1, 2, 4]
deque.removeLast(); // [3, 1, 2]
deque.removeFirst(); // [1, 2]
```
