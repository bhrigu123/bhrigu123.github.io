+++
title = "Lru Cache C++ Implementation"
date = "2017-01-22"
lastmode = "2020-07-11 16:05:26 +0530"
description = "LRU (Least Recently Used) algorithm implementation and explanation in C++"
tags = ["Programming"]
images = ["/images/others/lrucache.jpeg"]
aliases = ["/blog/2017/01/22/lru-cache-c-plus-plus-implementation"]
authors = ["Bhrigu"]
+++

LRU, or *Least Recetly Used*, is one of the [Page Replacement Algorithms](https://en.wikipedia.org/wiki/Page_replacement_algorithm), in which the system manages a given amount of memory - by making decisions what pages to keep in memory, and which ones to remove when the memory is full.  
<!--more-->

---
**Update**: I now have this article as a YouTube video tutorial also, where I talk about LRU, Data Structures and do hands on coding in **Java** (concept is pretty much same as C++). You can check out the video using below link:

* [LRU Cache - Explanation, Java Implementation and Demo](https://youtu.be/EmOIbVN0zBE)
---

**[contd. for C++]**

Let's say, the capacity of a given cache (memory) is *C*.

Our memory stores key, value pairs in it.


It should support the following operations:

* `get(key)` -  Get the value of the given key if it exists in the memory (else, let's say -1)

* `put(key, value)` - Set, or insert the value if not present. If our cache reaches its capacity, we should remove the item which was least recently used. 


Another constraint to the given problem is:<br>
Both the operations must be done in constant [Time Complexity](https://en.wikipedia.org/wiki/Time_complexity), ie in *O(1)*.


Now, we need to think of some of the data structures, which would allow us to perform the above operations in *O(1)*.


### Choice of data structures

* **Queue** - We should maintain a Queue (double ended queue), in which the most recently used pages (items) are in the front, and the least recently used pages are in the rear. This would allow to remove the least recently used item in *O(1)* time.

* **Doubly Linked List** - We should implement our Queue using a doubly linked list (instead of arrays), which would allow us to apply *shifting* operations in *O(1)* time. (like, when we need to shift a page to the front of the queue) 

* **HashMap** - We should hash the key values to the location where the page is stored. This would allow `get` operation in *O(1)* time.


### Design and Implementation

Now that we know which what all data structures to use, let's look at the implementation. 


Whenever a user `gets` a page, we return its value, and also move that page to the front of our Queue.


Whenever a user `sets` a page, if the page is already present, we update its value and move that page to the front of our Queue, <br>
else we add a new page to our cache in the front of the Queue.<br>
But if our cache has reached its capacity, we remove the least recently used page (ie the rear item in our Queue) from our memory.


1. `class Node`
   1. key
   2. value
   3. next node address
   4. previous node address
2. `class DoublyLinkedList`
  * Data members:
    1. front node address
    2. rear node address            
  * Member functions:
    1. move_page_to_head()
    2. remove_rear_page()
    3. get_rear_page()
    4. add_page_to_head()
3. `class LRUCache`
  * Data members:
    1. capacity
    2. current size
    3. a DoublyLinkedList object
    4. Hashmap
  * Member functions:
    1. get(key)
    2. put(key, value)


Let's make the 3 classes.


### Code

{{< gist bhrigu123 af96d2f734705ebbd8e050f190d01f17 >}}


### Running the code

Save the above code in a file, say of name `LRUCache.cpp`.

In the same directory create another `.cpp` file in which we will use get() and put() functions of our LRU. Paste the code below, compile & run it:


``` cpp RunLRUCache.cpp
#include <iostream>
#include "LRUCache.cpp"
using namespace std;

int main() {
	LRUCache cache(2);	// cache capacity 2
	cache.put(2,2);
	cout << cache.get(2) << endl;
	cout << cache.get(1) << endl;
	cache.put(1,1);
	cache.put(1,5);
	cout << cache.get(1) << endl;
	cout << cache.get(2) << endl;
	cache.put(8,8);
	cout << cache.get(1) << endl;
	cout << cache.get(8) << endl;

}

```  

<strong><u>Output:</u></strong>


``` sh output
2
-1
5
2
-1
8
```

The output comes out to be correct (you can check by creating a cache of size 2, and executing the given `get` and `put` functions in the above order.)


That is all for LRU Cache implementation - ie, the "Least Recently Used Page replacement algorithm".


`Notes:` 
> Use [unordered_map](http://www.cplusplus.com/reference/unordered_map/unordered_map/) instead of ordered maps as used above (ie just `map` was used above) to make it **_really_** O(1). To read difference: [unordered_map and map](http://www.geeksforgeeks.org/unordered_map-in-stl-and-its-applications/).

> The LRU Cache problem is available on Leetcode at: [LRU Cache](https://leetcode.com/problems/lru-cache/)
if you want to check it out.


Any feedback, doubts or questions, please leave in the comments. 
