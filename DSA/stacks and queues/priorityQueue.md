## Priority Queue

- A **Priority Queue** is a data structure where elements are stored in order based on their priority. 
- In this type of priority queue, elements are kept sorted so that the element with the highest priority is always at the front of the queue.

### Ways it can be implemented:
- **Min-Heap or Max-Heap**: Typically implemented using heaps, where a **min-heap** gives priority to the smallest element, and a **max-heap** gives priority to the largest element.
- **Singly Linked List**:
  - **Insert**: O(n) time complexity, as the list needs to be sorted after each insertion.
  - **Delete (or Dequeue)**: O(1) time complexity, as the highest priority element is always at the front.
  - **Space Complexity**: O(n)

### Time Complexities Summary:
| Operation      | Binary Heap | Fibonacci Heap |
|----------------|-------------|----------------|
| **Insert**     | O(log n)    | O(1) (amortized)|
| **Delete**     | O(log n)    | O(log n) (amortized)|
| **Peek**       | O(1)        | O(1)           |
| **Space**      | O(n)        | O(n)           |


### Operations:
1. **Insert**: Adds an element with a specific priority to the queue.
2. **Delete (or Dequeue)**: Removes the element with the highest priority (min or max) from the queue.
3. **Peek (or Front)**: Retrieves the element with the highest priority without removing it.
4. **Is Empty**: Checks if the priority queue is empty.
5. **Change Priority**: Updates the priority of an existing element (in some implementations).

### Applications:
- **Task Scheduling**: Priority queues are used in scheduling tasks based on their priority.
- **Dijkstra’s Shortest Path Algorithm**: Priority queues are used to select the next node to process in the graph traversal.
- **Huffman Encoding**: Priority queues are essential in the construction of Huffman trees used for data compression.
- **Real-time Systems**: Priority queues ensure that high-priority tasks are processed before lower-priority ones.

