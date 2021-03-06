# C++ Data Structures and Algorithms Cheat Sheet

## Table of Contents

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [C++ Data Structures and Algorithms Cheat Sheet](#c-data-structures-and-algorithms-cheat-sheet)
	- [Table of Contents](#table-of-contents)
	- [1.0 Data Structures](#10-data-structures)
		- [1.1 Overview](#11-overview)
		- [1.2 Vector `std::vector`](#12-vector-stdvector)
		- [1.3 Deque `std::deque`](#13-deque-stddeque)
		- [1.4 List `std::list` and `std::forward_list`](#14-list-stdlist-and-stdforward_list)
		- [1.5 Map `std::map` and `std::unordered_map`](#15-map-stdmap-and-stdunordered_map)
		- [1.6 Set `std::set`](#16-set-stdset)
		- [1.7 Stack `std::stack`](#17-stack-stdstack)
		- [1.8 Queue `std::queue`](#18-queue-stdqueue)
		- [1.9 Priority Queue `std::priority_queue`](#19-priority-queue-stdpriority_queue)
		- [1.10 Heap `std::priority_queue`](#110-heap-stdpriority_queue)
		- [1.11 String `std::string`](#111-string-stdstring)
	- [2.0 Trees](#20-trees)
		- [2.1 Binary Tree](#21-binary-tree)
		- [2.2 Balanced Trees](#22-balanced-trees)
		- [2.3 Binary Search](#23-binary-search)
		- [2.4 Depth-First Search](#24-depth-first-search)
		- [2.5 Breadth-First Search](#25-breadth-first-search)
	- [3.0 NP Complete Problems](#30-np-complete-problems)
		- [3.1 NP Complete](#31-np-complete)
		- [3.2 Traveling Salesman Problem](#32-traveling-salesman-problem)
		- [3.3 Knapsack Problem](#33-knapsack-problem)
	- [4.0 Sorting Algorithms](#40-sorting-algorithms)
		- [4.1 Insertion Sort](#41-insertion-sort)
		- [4.2 Selection Sort](#42-selection-sort)
		- [4.3 Bubble Sort](#43-bubble-sort)
		- [4.4 Merge Sort](#44-merge-sort)
		- [4.5 Quicksort](#45-quicksort)
	- [5.0 Searching Algorithms](#50-searching-algorithms)
		- [5.1 Sequential Search](#51-sequential-search)
		- [5.2 Binary Search](#52-binary-search)
		- [5.3 Depth-first Search](#53-depth-first-search)
		- [5.4 Breadth-first Search](#54-breadth-first-search)
	- [6.0 Concepts](#60-concepts)
		- [6.1 Abstraction](#61-abstraction)
		- [6.2 Encapsulation](#62-encapsulation)
		- [6.3 Inheritance](#63-inheritance)
		- [6.4 Polymorphism](#64-polymorphism)	
		- [6.5 Virtual Functions](#65-virtual-functions)	
		- [6.6 Miscellaneous](#66-miscellaneous)			

<!-- /TOC -->


## 1.0 Data Structures
### 1.1 Overview

![Legend](General/Legend.png)

![DataStructures](General/DataStructures.png)

![ComplexityChart](General/ComplexityChart.png)

![DataStructureSelection](General/DataStructuresSelection.png)

-------------------------------------------------------
### 1.2 Vector `std::vector`
**Use for**
* Simple storage
* Adding but not deleting
* Serialization
* Quick lookups by index
* Easy conversion to C-style arrays
* Efficient traversal (contiguous CPU caching)

**Do not use for**
* Insertion/deletion in the middle of the list
* Dynamically changing storage
* Non-integer indexing

**Time Complexity**

| Operation    | Time Complexity |
|--------------|-----------------|
| Insert Head  |          `O(n)` |
| Insert Index |          `O(n)` |
| Insert Tail  |          `O(1)` |
| Remove Head  |          `O(n)` |
| Remove Index |          `O(n)` |
| Remove Tail  |          `O(1)` |
| Find Index   |          `O(1)` |
| Find Object  |          `O(n)` |

**Example Code**
```c++
std::vector<int> v;

//---------------------------------
// General Operations
//---------------------------------

//Insert head, index, tail
v.insert(v.begin(), value);             //head
v.insert(v.begin() + index, value);     //index
v.push_back(value);                     //tail

//Access head, index, tail
int head = v.front();       //head
int value = v.at(index);    //index
int tail = v.back();        //tail

//Size
unsigned int size = v.size();

//Iterate
for(std::vector<int>::iterator it = v.begin(); it != v.end(); it++) {
    std::cout << *it << std::endl;
}

//Remove head, index, tail
v.erase(v.begin());             //head
v.erase(v.begin() + index);     //index
v.pop_back();                   //tail

//Subarray
vector<int> subarray_A(A.begin() + i, A. begin() + j ) // sets sub array A to be A[i : j - 1].

//Key methods in algorithms
binary_search(A. begin(), A.end(), 42);
lower_bound(A.begin(), A.end(), 42);
upper_bound(A.begin(), A.end(), 42);
fill(A.begin(), A.end(), 42);
swap(x, y);
min_element(A.begin(), A.end()), max_element(A.begin(), A.end());
reverse(A.begin(), A.end()), rotate(A.begin(), A.begin() +shift, A.end());
sort(A.begin(), A.end());

//Clear
v.clear();
```

-------------------------------------------------------
### 1.3 Deque `std::deque`
**Use for**
* Similar purpose of `std::vector`
* Basically `std::vector` with efficient `push_front` and `pop_front`

**Do not use for**
* C-style contiguous storage (not guaranteed)

**Notes**
* Pronounced 'deck'
* Stands for **D**ouble **E**nded **Que**ue

**Example Code**
```c++
std::deque<int> d;

//---------------------------------
// General Operations
//---------------------------------

//Insert head, index, tail
d.push_front(value);                    //head
d.insert(d.begin() + index, value);     //index
d.push_back(value);                     //tail

//Access head, index, tail
int head = d.front();       //head
int value = d.at(index);    //index
int tail = d.back();        //tail

//Size
unsigned int size = d.size();

//Iterate
for(std::vector<int>::iterator it = d.begin(); it != d.end(); it++) {
    std::cout << *it << std::endl;
}

//Remove head, index, tail
d.pop_front();                  //head
d.erase(d.begin() + index);     //index
d.pop_back();                   //tail

//Clear
d.clear();
```

-------------------------------------------------------
### 1.4 List `std::list` and `std::forward_list`
**Use for**
* Insertion into the middle/beginning of the list
* Efficient sorting (pointer swap vs. copying)

**Do not use for**
* Direct access

**Time Complexity**

| Operation    | Time Complexity |
|--------------|-----------------|
| Insert Head  |          `O(1)` |
| Insert Index |          `O(n)` |
| Insert Tail  |          `O(1)` |
| Remove Head  |          `O(1)` |
| Remove Index |          `O(n)` |
| Remove Tail  |          `O(1)` |
| Find Index   |          `O(n)` |
| Find Object  |          `O(n)` |

**Example Code**
```c++
std::list<int> l;

//---------------------------------
// General Operations
//---------------------------------

//Insert head, index, tail
l.push_front(value);                    //head
l.insert(l.begin() + index, value);     //index
l.push_back(value);                     //tail

//Access head, index, tail
int head = l.front();                                           //head
int value = std::list<int>::iterator it = l.begin() + index;    //index
int tail = l.back();                                            //tail

//Size
unsigned int size = l.size();

//Iterate
for(std::list<int>::iterator it = l.begin(); it != l.end(); it++) {
    std::cout << *it << std::endl;
}

//Remove head, index, tail
l.pop_front();                  //head
l.erase(l.begin() + index);     //index
l.pop_back();                   //tail

//Clear
l.clear();

//---------------------------------
// Container-Specific Operations
//---------------------------------

//Splice: Transfer elements from list to list
//  splice(iterator pos, list &x) transfers all the elements of x into the container
//  splice(iterator pos, list &x, iterator i) transfers only the element pointed by i from x into the container
//  splice(iterator pos, list &x, iterator first, iterator last) transfers the range [first,last) from x into the container
l.splice(l.begin() + index, list2); // transfer elements of list2 into l at index

//Remove: Remove an element by value
l.remove(value);

//Unique: Remove duplicates
l.unique();

//Merge: Merge two sorted lists
l.merge(list2);

//Sort: Sort the list
l.sort();

//Reverse: Reverse the list order
l.reverse();
```

-------------------------------------------------------
### 1.5 Map `std::map` and `std::unordered_map`
**Use for**
* Key-value pairs
* Constant lookups by key
* Searching if key/value exists
* Removing duplicates
* `std::map`
    * Ordered map
* `std::unordered_map`
    * Hash table

**Do not use for**
* Sorting

**Notes**
* Typically ordered maps (`std::map`) are slower than unordered maps (`std::unordered_map`)
* Maps are typically implemented as *binary search trees*

**Time Complexity**

**`std::map`**

| Operation           | Time Complexity |
|---------------------|-----------------|
| Insert              |     `O(log(n))` |
| Access by Key       |     `O(log(n))` |
| Remove by Key       |     `O(log(n))` |
| Find/Remove Value   |     `O(log(n))` |

**`std::unordered_map`**

| Operation           | Time Complexity |
|---------------------|-----------------|
| Insert              |          `O(1)` |
| Access by Key       |          `O(1)` |
| Remove by Key       |          `O(1)` |
| Find/Remove Value   |              -- |

**Example Code**
```c++
std::map<std::string, std::string> m;

//---------------------------------
// General Operations
//---------------------------------

//Insert
m.insert(std::pair<std::string, std::string>("key", "value"));

//Access key, value
std::string value = m.at("key");
std::string value = m["key"];

//Size
unsigned int size = m.size();

//Iterate
for(std::map<int>::iterator it = m.begin(); it != m.end(); it++) {
    std::cout << "key"*it << std::endl;
}

//Remove 
m.erase("key");

//Clear
m.clear();

//---------------------------------
// Container-Specific Operations
//---------------------------------

//Find if an element exists by key
bool exists = (m.find("key") != m.end());

//Count the number of elements with a certain key
unsigned int count = m.count("key");
```

-------------------------------------------------------
### 1.6 Set `std::set`
**Use for**
* Removing duplicates
* Ordered dynamic storage

**Do not use for**
* Simple storage
* Direct access by index

**Notes**
* Sets are often implemented with binary search trees

**Time Complexity**

| Operation    | Time Complexity |
|--------------|-----------------|
| Insert       |     `O(log(n))` |
| Remove       |     `O(log(n))` |
| Find         |     `O(log(n))` |

**Example Code**
```c++
std::set<int> s;

//---------------------------------
// General Operations
//---------------------------------

//Insert
s.insert(20);

//Size
unsigned int size = s.size();

//Iterate
for(std::set<int>::iterator it = s.begin(); it != s.end(); it++) {
    std::cout << *it << std::endl;
}

//Remove
s.remove(20);

//Clear
s.clear();

//---------------------------------
// Container-Specific Operations
//---------------------------------

//Find if an element exists
bool exists = (s.find(20) != s.end());

//Count the number of elements with a certain value
unsigned int count = s.count(20);
```

-------------------------------------------------------
### 1.7 Stack `std::stack`
**Use for**
* First-In Last-Out operations
* Reversal of elements

**Time Complexity**

| Operation    | Time Complexity |
|--------------|-----------------|
| Push         |          `O(1)` |
| Pop          |          `O(1)` |
| Top          |          `O(1)` |

**Example Code**
```c++
std::stack<int> s;

//---------------------------------
// Container-Specific Operations
//---------------------------------

//Push
s.push(20);

//Size
unsigned int size = s.size();

//Pop
s.pop();

//Top
int top = s.top();
```

-------------------------------------------------------
### 1.8 Queue `std::queue`
**Use for**
* First-In First-Out operations
* Ex: Simple online ordering system (first come first served)
* Ex: Semaphore queue handling
* Ex: CPU scheduling (FCFS)

**Notes**
* Often implemented as a `std::deque`

**Example Code**
```c++
std::queue<int> q;

//---------------------------------
// General Operations
//---------------------------------

//Insert
q.push(value);

//Access head, tail
int head = q.front();       //head
int tail = q.back();        //tail

//Size
unsigned int size = q.size();

//Remove
q.pop();
```

-------------------------------------------------------
### 1.9 Priority Queue `std::priority_queue`
**Use for**
* First-In First-Out operations where **priority** overrides arrival time
* Ex: CPU scheduling (smallest job first, system/user priority)
* Ex: Medical emergencies (gunshot wound vs. broken arm)

**Notes**
* Often implemented as a `std::vector`

**Example Code**
```c++
std::priority_queue<int> p;

//---------------------------------
// General Operations
//---------------------------------

//Insert
p.push(value);

//Access
int top = p.top();  //`Top` element

//Size
unsigned int size = p.size();

//Remove
p.pop();
```

-------------------------------------------------------
### 1.10 Heap `std::priority_queue`
**Notes**
* A heap is essentially an instance of a priority queue
* A **min** heap is structured with the root node as the smallest and each child subsequently smaller than its parent
* A **max** heap is structured with the root node as the largest and each child subsequently larger than its parent
* A min heap could be used for *Smallest Job First* CPU Scheduling
* A max heap could be used for *Priority* CPU Scheduling

**Max Heap Example (using a binary tree)**

![MaxHeap](General/MaxHeap.png)

-------------------------------------------------------
### 1.11 String `std::string`
**Notes**

```c++
std::string str;

//---------------------------------
// General Operations
//---------------------------------

// Append chars to string
str.append("Gauss");

// Append char to string
str.push_back('c');

// Delete last character
str.pop_back();

// Insert chars in string
str.insert(s.begin() + shift, "Gauss");

// Position of chars in string
std::size_t pos = str.find("live");

// Get substring
std::string newStr = str.substr(pos, len);

// Compare two strings
// 0 equal
// <0 Either the value of the first character that does not match is lower in the compared string, or all compared characters match but the compared string is shorter.
// >0 Either the value of the first character that does not match is greater in the compared string, or all compared characters match but the compared string is longer.
int result = std.compare("Compared String")
```

-------------------------------------------------------
## 2.0 Trees
### 2.1 Binary Tree
* A binary tree is a tree with at most two (2) child nodes per parent
* Binary trees are commonly used for implementing `O(log(n))` operations for ordered maps, sets, heaps, and binary search trees
* Binary trees are **sorted** in that nodes with values greater than their parents are inserted to the **right**, while nodes with values less than their parents are inserted to the **left**

**Binary Search Tree**

![BinarySearchTree](General/BinarySearchTree.png)

-------------------------------------------------------
### 2.2 Balanced Trees
* Balanced trees are a special type of tree which maintains its balance to ensure `O(log(n))` operations
* When trees are not balanced the benefit of `log(n)` operations is lost due to the highly vertical structure
* Examples of balanced trees:
    * AVL Trees
    * Red-Black Trees

-------------------------------------------------------
### 2.3 Binary Search
**Idea:**
1. If current element, return
2. If less than current element, look left
3. If more than current element, look right
4. Repeat

**Data Structures:**
* Tree
* Sorted array

**Space:**
* `O(1)`

**Best Case:**
* `O(1)`

**Worst Case:**
* `O(log n)`

**Average:**
* `O(log n)`

**Visualization:**

![BinarySearch](Searching/Animations/BinarySearch.gif)

-------------------------------------------------------
### 2.4 Depth-First Search
**Idea:**
1. Start at root node
2. Recursively search all adjacent nodes and mark them as searched
3. Repeat

**Data Structures:**
* Tree
* Graph

**Space:**
* `O(V)`, `V = number of verticies`

**Performance:**
* `O(E)`, `E = number of edges`

**Visualization:**

![DepthFirstSearch](Searching/Animations/Depth-FirstSearch.gif)

-------------------------------------------------------
### 2.5 Breadth-First Search
**Idea:**
1. Start at root node
2. Search neighboring nodes first before moving on to next level

**Data Structures:**
* Tree
* Graph

**Space:**
* `O(V)`, `V = number of verticies`

**Performance:**
* `O(E)`, `E = number of edges`

**Visualization:**

![DepthFirstSearch](Searching/Animations/Breadth-FirstSearch.gif)
-------------------------------------------------------
## 3.0 NP Complete Problems
### 3.1 NP Complete
* **NP Complete** means that a problem is unable to be solved in **polynomial time**
* NP Complete problems can be *verified* in polynomial time, but not *solved*

-------------------------------------------------------
### 3.2 Traveling Salesman Problem
**Idea:**
* Visit all cities from list
* Distances between cities known
* Shortest possible route to visit all cities once and return to origin city?

**Solution**
* Start at city *1*, visit cities until at *j*.
* Divide into sub-problems and keep track of cities visited.

**Analysis**
* At most *2<sup>n</sup>⋅n* sub-probelms and each one takes linear time, so total runtime is *O(2<sup>n</sup>⋅n<sup>2</sup>)*.

[More info](https://www.tutorialspoint.com/design_and_analysis_of_algorithms/design_and_analysis_of_algorithms_travelling_salesman_problem.htm)

-------------------------------------------------------
### 3.3 Knapsack Problem
[Info](https://www.tutorialspoint.com/design_and_analysis_of_algorithms/design_and_analysis_of_algorithms_01_knapsack.htm)

-------------------------------------------------------
## 4.0 Sorting Algorithms
###  4.1 Insertion Sort
**Idea:**
1. Iterate over all elements
2. For each element:
    * Check if element is larger than largest value in sorted array
3. If larger: Move on
4. If smaller: Move item to correct position in sorted array

**Data structure:**
* Array

**Space:**
* O(1)

**Best Case:**
* Already sorted
* O(n)

**Worst Case:**
* Reverse sorted
* O(n^2)

**Average:**
* O(n^2)

**Advantages**
* Easy to code
* Intuitive
* Better than selection sort and bubble sort for small data sets
* Can sort in-place

**Disadvantages**
* Very inefficient for large datasets

**Visualization**

![InsertionSort](Sorting/Animations/InsertionSort.gif)

-------------------------------------------------------
### 4.2 Selection Sort
**Idea:**
1. Iterate over all elements
2. For each element:
    * If smallest element of unsorted sublist, swap with left-most unsorted element

**Data structure:**
* Array

**Space:**
* O(1)

**Best Case:**
* Already sorted
* O(n^2)

**Worst Case:**
* Reverse sorted
* O(n^2)
    
**Average:**
* O(n^2)

**Advantages**
* Simple
* Can sort in-place
* Low memory usage for small datasets

**Disadvantages**
* Very inefficient for large datasets

**Visualization**

![SelectionSort](Sorting/Animations/SelectionSort.gif)

![SelectionSort](Sorting/Animations/SelectionSort2.gif)

-------------------------------------------------------
### 4.3 Bubble Sort
**Idea:**
1. Iterate over all elements
2. For each element:
    * Swap with next element if out of order
3. Repeat until no swaps needed

**Data structure:**
* Array

**Space:**
* O(1)

**Best Case:**
* Already sorted
* O(n)
    
**Worst Case:**
* Reverse sorted
* O(n^2)
    
**Average:**
* O(n^2)

**Advantages**
* Easy to detect if list is sorted

**Disadvantages**
* Very inefficient for large datasets
* Much worse than even insertion sort

**Visualization**

![BubbleSort](Sorting/Animations/BubbleSort.gif)

-------------------------------------------------------
### 4.4 Merge Sort
**Idea:**
1. Divide list into smallest unit (1 element)
2. Compare each element with the adjacent list
3. Merge the two adjacent lists
4. Repeat

**Data structure:**
* Array

**Space:**
* O(n) auxiliary

**Best Case:**
* O(nlog(n))
    
**Worst Case:**
* Reverse sorted
* O(nlog(n))
    
**Average:**
* O(nlog(n))

**Advantages**
* High efficiency on large datasets
* Nearly always O(nlog(n))
* Can be parallelized
* Better space complexity than standard Quicksort

**Disadvantages**
* Still requires O(n) extra space
* Slightly worse than Quicksort in some instances

**Visualization**

![MergeSort](Sorting/Animations/MergeSort.gif)

![MergeSort](Sorting/Animations/MergeSort2.gif)

**Example Code**
```
int[] mergeSort(int[] array) {
  if (array.length <= 1)
    return array;
  int middle = array.length / 2;
  int firstHalf = mergeSort(array[0..middle - 1]);
  int secondHalf = mergeSort(array[middle..array.length - 1]);
  return merge(firstHalf, secondHalf);
}
```

-------------------------------------------------------
### 4.5 Quicksort
**Idea:**
1. Choose a **pivot** from the array
2. Partition: Reorder the array so that all elements with values *less* than the pivot come before the pivot, and all values *greater* than the pivot come after
3. Recursively apply the above steps to the sub-arrays

**Data structure:**
* Array

**Space:**
* O(n)

**Best Case:**
* O(nlog(n))

**Worst Case:**
* All elements equal
* O(n^2)

**Average:**
* O(nlog(n))

**Advantages**
* Can be modified to use O(log(n)) space
* Very quick and efficient with large datasets
* Can be parallelized
* Divide and conquer algorithm

**Disadvantages**
* Not stable (could swap equal elements)
* Worst case is worse than Merge Sort

**Optimizations**
Choice of pivot:
* Choose median of the first, middle, and last elements as pivot
* Counters worst-case complexity for already-sorted and reverse-sorted

**Visualization**

![QuickSort](Sorting/Animations/Quicksort.gif)

**Example Code**
```
void quicksort(int[] array, int startIndex, int endIndex) {
  if (startIndex >= endIndex) {
    // Base case (array segment has 1 or 0 elements)
  } else {
    int pivotIndex = partition(array, startIndex, endIndex);
    quicksort(array, startIndex, pivotIndex - 1);
    quicksort(array, pivotIndex + 1, endIndex);
  }
}
```

-------------------------------------------------------
## 5.0 Searching Algorithms
[Info](https://beginnersbook.com/2013/03/oops-in-java-encapsulation-inheritance-polymorphism-abstraction/)

-------------------------------------------------------
### 5.1 Sequential Search
**Idea:**
* Start from the leftmost element of arr[] and one by one compare x with each element of arr[]
* If x matches with an element, return the index.
* If x doesn’t match with any of elements, return -1.

**Data Structure:** Array and linked list

**Worst Case:** O(n)

-------------------------------------------------------
### 5.2 Binary Search
**Idea:**
* Search a sorted array by repeatedly dividing the search interval in half.
* Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise narrow it to the upper half.
* Repeatedly check until the value is found or the interval is empty.

**Data Structure:** Sorted array and binary search tree

**Worst Case:** O(log(n))

-------------------------------------------------------
### 5.3 Depth-first Search
(DFS)

**Idea:**
* One starts at the root (selecting some arbitrary node as the root in the case of a graph) and explores as far as possible along each branch before backtracking.

**Data Structure:** Graph of |V| vertices and |E| edges

**Worst Case:** O(|V| + |E|)

-------------------------------------------------------
### 5.4 Breadth-first Search
(BFS)

**Idea:**
*  It starts at the tree root (or some arbitrary node of a graph, sometimes referred to as a 'search key'[1]) and explores the neighbor nodes first, before moving to the next level neighbours.

**Data Structure:** Graph of |V| vertices and |E| edges

**Worst Case:** O(|V| + |E|)

-------------------------------------------------------
## 6.0 Concepts
[Info](https://beginnersbook.com/2013/03/oops-in-java-encapsulation-inheritance-polymorphism-abstraction/)

-------------------------------------------------------
### 6.1 Abstraction
**Idea:**
* The process of generalization.
* A process where you show only the "relevant" data and "hide" unnecessary details of an object from the user.

**Examples:**
* A car is composed of several other smaller objects like a gearing system, steering mechanism, engine, which are again have their own subsystems. But for humans car is a one single object, and they only need to know what parts do (i.e. gas petal, brake, gear shift) instead of how they do it.
* When logging into Goolge account, need to know username and password. Do not need to know how information is sent to server, etc.

-------------------------------------------------------
### 6.2 Encapsulation
(Data Hiding) - the hiding of implementation details

**Idea:**
* Binding the data with the code that manipulates it.
* Keeping the data and the code safe from external interference.

**Characteristics:**
* Everyone knows how to access it.
* Can be easily used regardless of implementation details.
* No side effects.

**Examples:**
* Every function is an encapsulation.
* Power steering of a car is a complex system, which internally have lots of components tightly coupled together, they work synchronously to turn the car in the desired direction. It even controls the power delivered by the engine to the steering wheel. But to the external world there is only one interface is available and rest of the complexity is hidden. Moreover, the steering unit in itself is complete and independent. It does not affect the functioning of any other mechanism.
* User only knows that he can store data in the form of key/value pair in a Hashtable and that he can retrieve that data in the various ways. But the actual implementation like, how and where this data is actually stored, is hidden from the user. User can simply use Hashtable wherever he wants to store Key/Value pairs without bothering about its implementation.

-------------------------------------------------------
### 6.3 Inheritance

**Idea:**
* Mechanism by which an object acquires some/all properties of another object.
* Hierarchical classification.

**Examples:**
* Car is a four wheeler vehicle so assume that we have a class FourWheeler and a sub class of it named Car. Here Car acquires the properties of a class FourWheeler. 

-------------------------------------------------------
### 6.4 Polymorphism

**Idea:**
* To process objects differently based on their data type.
* Literally: "many forms"
* The ability of one method to have different behavior depending on the type of object it is being called on or the type of object being passed as a parameter.
* Implemented by designing a generic interface, which provides generic methods for a certain class of action. Can be multiple classes which provide the implementation of these generic methods.

**Examples:**
* A car has a gear transmission system. It has four front gears and one backward gear. When the engine is accelerated, movement and power are delivered depending upon which gear is engaged. The action is same (pressing gas petal) but based the type of gear changes the action (forward, backward, etc.).
* A method that does addition works for different data types (i.e. integer, float, etc.).

**Static: Method Overloading**
* More than one method having the same name, but behave differently based on arguments passed.
* Decided at compile time.

**Dynamic: Method Overriding**
* A derived class is implementing a method of its super class.
* Decided at runtime.

-------------------------------------------------------
### 6.5 Virtual Functions

**Idea:**
* The implementation for a method is selected according to the type of the object as opposed to the type of the reference.
* Describes function behavior when working with superclasses and subclasses.
* Virtual methods are used for polymorphism: They allow a single method call to invoke different method definitions based on the class of the object.

**Example:** Assume class B is a subclass of class A. Also assume both classes A and B have a method `bar()`. Let's say we have the following code in C++:

```
A *foo = new B();
foo->bar();
```

If the method `bar()` is declared to be virtual in class A, then when we call `foo‐>bar()`, the method found in class B will be run. However, if the method `bar()` is not declared to be virtual, then this code will run the method found in class A when we call `foo‐>bar()`.

-------------------------------------------------------
### 6.6 Miscellaneous

**Model-View-Controller**: a program that uses separate programming entities to store the data (the "model"), to display the data (the "view"), and to modify the data (the "controller").

