# DYNAMIC ARRAYS
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
# STACKS AND QUEUES
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
import java.util.Queue;
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
import java.util.Deque;
ArrayDeque<Integer> deque = new ArrayDeque<Integer>();
deque.addFirst(1); // [1]
deque.addLast(2); // [1, 2]
deque.addFirst(3); // [3, 1, 2]
deque.addFirst(4); // [3, 1, 2, 4]
deque.removeLast(); // [3, 1, 2]
deque.removeFirst(); // [1, 2]
```
## [Priority Queues](https://docs.oracle.com/javase/8/docs/api/java/util/PriorityQueue.html)
**A priority queue supports the following operations: insertion of elements, deletion of
the element considered highest priority, and retrieval of the highest priority element, all in
O(log n) time according to the number of elements in the priority queue. Priority is based on
a comparator function, but** ***by default the lowest element is at the front of the priority queue***.
**The priority queue is one of the most important data structures in competitive programming,
so make sure you understand how and when to use it. By default, the Priority Queue puts
the lowest element at the front of the queue.**
```java
import java.util.PriorityQueue;
PriorityQueue<Integer> pq = new PriorityQueue<Integer>();
pq.add(4); // [4]
pq.add(2); // [4, 2]
pq.add(1); // [4, 2, 1]
pq.add(3); // [4, 3, 2, 1]
System.out.println(pq.peek()); // 1
pq.poll(); // [4, 3, 2]
pq.poll(); // [4, 3]
pq.add(5); // [5, 4, 3]
```
# SETS
**A set is a collection of objects that contains no duplicates. There are two types of sets:
unordered sets (```HashSet``` in Java), and ordered set (```TreeSet``` in Java).**
## [HashSets (UnOrdered Sets)](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html)
**The unordered set works by hashing, which is assigning a usually-unique code to every
variable/object which allows insertions, deletions, and searches in O(1) time, albeit with a
high constant factor, as hashing requires a large constant number of operations. However,
as the name implies, elements are not ordered in any meaningful way, so traversals of an
unordered set will return elements in some arbitrary order. The operations on an unordered
set are ```add```, which adds an element to the set if not already present, ```remove```, which deletes
an element if it exists, and ```contains```, which checks whether the set contains that element.**
```java
import java.util.HashSet;
HashSet<Integer> set = new HashSet<Integer>();
set.add(1); // [1]
set.add(4); // [1, 4] in arbitrary order
set.add(2); // [1, 4, 2] in arbitrary order
set.add(1); // [1, 4, 2] in arbitrary order
// the add method did nothing because 1 was already in the set
System.out.println(set.contains(1)); // true
set.remove(1); // [2, 4] in arbitrary order
System.out.println(set.contains(5)); // false
set.remove(0); // [2, 4] in arbitrary order
// if the element to be removed does not exist, nothing happens
for(int element : set){
System.out.println(element);
}
// You can iterate through an unordered set, but it will do so in arbitrary order
```
## [TreeSets (Ordered Sets)](https://docs.oracle.com/javase/8/docs/api/java/util/TreeSet.html)
**The second type of set data structure is the ordered or sorted set. Insertions, deletions,
and searches on the ordered set require O(log n) time, based on the number of elementsin the set. As well as those supported by the unordered set, the ordered set also allows four additional operations: ```first```, which returns the lowest element in the set, ```last```, which
returns the highest element in the set, ```lower```, which returns the greatest element strictly less
than some element, and ```higher```, which returns the least element strictly greater than it.**</br>
**The primary limitation of the ordered set is that we can’t efficiently access the kth largest
element in the set, or find the number of elements in the set greater than some arbitrary x.**
```java
import java.util.TreeSet;
TreeSet<Integer> set = new TreeSet<Integer>();
set.add(1); // [1]
set.add(14); // [1, 14]
set.add(9); // [1, 9, 14]
set.add(2); // [1, 2, 9, 14]
System.out.println(set.higher(7)); // 9
System.out.println(set.higher(9)); // 14
System.out.println(set.lower(5)); // 2
System.out.println(set.first()); // 1
System.out.println(set.last()); // 14
set.remove(set.higher(6)); // [1, 2, 14]
System.out.println(set.higher(23); // ERROR, no such element exists
```
# MAPS
**A map is a set of ordered pairs, each containing a key and a value. In a map, all keys
are required to be unique, but values can be repeated. Maps have three primary methods:
one to add a specified key-value pairing, one to retrieve the value for a given key, and one
to remove a key-value pairing from the map. Like sets, maps can be unordered (```HashSet```
in Java) or ordered (```TreeSet``` in Java). In an unordered map, hashing is used to support
O(1) operations. In an ordered map, the entries are sorted in order of key. Operations are
O(log n), but accessing or removing the next key higher or lower than some input k is also
supported**
## [HashMaps (UnOrdered Maps)](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html)
**In the unordered map, the ```put(key, value)``` method assigns a value to a key and places
the key and value pair into the map. The ```get(key)``` method returns the value associated with
the key. The ```containsKey(key)``` method checks whether a key exists in the map. Lastly,
```remove(key)``` removes the map entry associated with the specified key. All of these operations
are O(1), but again, due to the hashing, this has a high constant factor.**
```java
import java.util.HashMap;
HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
map.put(1, 5); // [(1, 5)]
map.put(3, 14); // [(1, 5); (3, 14)]
map.put(2, 7); // [(1, 5); (3, 14); (2, 7)]
map.remove(2); // [(1, 5); (3, 14)]
System.out.println(map.get(1)); // 5
System.out.println(map.containsKey(7)); // false
System.out.println(map.containsKey(1)); // true
```
## [TreeMaps (Ordered Maps)](https://docs.oracle.com/javase/8/docs/api/java/util/TreeMap.html)
**The ordered map supports all of the operations that an unordered map supports, and
additionally supports firstKey/firstEntry and lastKey/lastEntry, returning the lowest
key/entry and the highest key/entry, as well as higherKey/higherEntry and lowerKey/
lowerEntry, returning the lowest key/entry strictly higher than the specified key, or the
highest key/entry strictly lower than the specified key.**</br>
A note on unordered sets and maps: In USACO contests, they’re generally fine, but in
CodeForces contests, you should always use sorted sets and maps. This is because the built-in
hashing algorithm is vulnerable to pathological data sets causing abnormally slow runtimes,
in turn causing failures on some test cases.
```java
TreeMap<Integer, Integer> map = new TreeMap<Integer, Integer>();
map.put(3, 5); // [(3, 5)]
map.put(11, 4); // [(3, 5); (11, 4)]
map.put(10, 491); // [(3, 5); (10, 491); (11, 4)]
System.out.println(map.firstKey()); // 3
System.out.println(map.firstEntry()); // (3, 5)
System.out.println(map.lastEntry()); // (11, 4)
System.out.println(map.higherEntry(4)); // (10, 491)
map.remove(11); // [(3, 5); (10, 491)]
System.out.println(map.lowerKey(4)); // 3
System.out.println(map.lowerKey(3)); // ERROR
```
## MultiSets
**Lastly, there is the multiset, which is essentially a sorted set that allows multiple copies
of the same element. While there is no ```Multiset``` in Java, we can implement one using the
```TreeMap``` from values to their respective frequencies. We declare the ```TreeMap``` implementation
globally so that we can write functions for adding and removing elements from it.**</br>
**The first, last, higher, and lower operations still function as intended; just use ```firstKey```,
```lastKey```, ```higherKey```, and ```lowerKey``` respectively**
```java
static TreeMap<Integer, Integer> multiset = new TreeMap<Integer, Integer>();
public static void main(String[] args){
...
}
static void add(int x){
  if(multiset.containsKey(x)){
  multiset.put(x, multiset.get(x) + 1);
  } else {
    multiset.put(x, 1);
  }
}
static void remove(int x){
  multiset.put(x, multiset.get(x) - 1);
  if(multiset.get(x) == 0){
    multiset.remove(x);
  }
}
```
![Time-Complexity-of-these-Data-Structures](https://github.com/welterskelter/notes/blob/1916bd56ec0b7eb1f9f1b3c57de8f247cf4bf99f/images/BigO_cheatsheet.jpg?raw=true)
