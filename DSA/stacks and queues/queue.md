### Queue Data Structure

A **Queue** is a linear data structure that follows the **First In, First Out (FIFO)** principle. This means that the element added first will be the first one to be removed.

## Operations of a Queue
1. **Enqueue**: Add an element to the end of the queue.
2. **Dequeue**: Remove an element from the front of the queue.
3. **Front**: View the front element without removing it.
4. **IsEmpty**: Check if the queue is empty.
5. **IsFull**: Check if the queue is full (for array-based implementations).

## There are four different types of queues:

- Simple Queue
- Circular Queue
- Priority Queue
- Double Ended Queue


### Applications of Queue

- CPU scheduling, Disk Scheduling
- When data is transferred asynchronously between two processes.The queue is used for synchronization. For example: IO Buffers, pipes, file IO, etc
- Handling of interrupts in real-time systems.
- Call Center phone systems use Queues to hold people calling them in order.

## Types of Queue Implementations

### 1. **Array-based Queue**
- A queue can be implemented using a fixed-size array.
- The front of the queue and the rear are tracked by indices.

### 2. **Linked List-based Queue**
- A queue can also be implemented using a linked list.
- The **front** is the head of the list, and the **rear** is the tail of the list.
- Dynamic resizing occurs naturally as new nodes are added and removed.

---

## Array-based Queue Implementation in C

```c
#include <stdio.h>
#include <stdlib.h>

#define MAX 5 // Maximum size of the queue

// Define the queue structure
struct Queue {
    int arr[MAX];
    int front;
    int rear;
};

// Initialize the queue
void initQueue(struct Queue* q) {
    q->front = -1;
    q->rear = -1;
}

// Check if the queue is empty
int isEmpty(struct Queue* q) {
    return (q->front == -1);
}

// Check if the queue is full
int isFull(struct Queue* q) {
    return (q->rear == MAX - 1);
}

// Enqueue operation (add an element to the queue)
void enqueue(struct Queue* q, int value) {
    if (isFull(q)) {
        printf("Queue is full!\n");
        return;
    }
    if (q->front == -1) {
        q->front = 0; // First element inserted
    }
    q->rear++;
    q->arr[q->rear] = value;
    printf("%d enqueued to the queue\n", value);
}

// Dequeue operation (remove an element from the queue)
int dequeue(struct Queue* q) {
    if (isEmpty(q)) {
        printf("Queue is empty!\n");
        return -1;
    }
    int dequeuedValue = q->arr[q->front];
    if (q->front == q->rear) { // A single value in queue
        q->front = q->rear = -1; // Reset queue when it becomes empty
    } else {
        q->front++;
    }
    return dequeuedValue;
}

// Display the queue
void displayQueue(struct Queue* q) {
    if (isEmpty(q)) {
        printf("Queue is empty!\n");
        return;
    }
    printf("Queue elements: ");
    for (int i = q->front; i <= q->rear; i++) {
        printf("%d ", q->arr[i]);
    }
    printf("\n");
}

int main() {
    struct Queue q;
    initQueue(&q);

    enqueue(&q, 10);
    enqueue(&q, 20);
    enqueue(&q, 30);

    displayQueue(&q);

    printf("%d dequeued from the queue\n", dequeue(&q));

    displayQueue(&q);

    return 0;
}
```

## Linked List implementation of a Queue

```c
// Linked List implementation of a queue

#include <stdio.h>
#include <stdlib.h>


typedef struct Node{

    int val;
    struct Node *next;

} Node;

Node *head = NULL;


void enqueue(int val){ // Insert at the beginning
    Node *node = (struct Node *) malloc(sizeof (Node));

    if (head == NULL){
        head = node;
    }else{
        Node *h = head;
        while (h->next!=NULL){
            h = h->next;
        }
        h->next = node;
        node->val = val;
    }
}

void dequeue(){ // Remove from the END

    if (head == NULL){
        printf("Empty List... Exiting");
        exit(-1);
    } else{
        Node *h = head;
        while (h->next->next !=NULL){
            h = h->next;
        }
        h->next = NULL;
    }
}

void print(){
    Node *h = head;
    while (h!=NULL){
        printf("val: %d -> \t", h->val);
        h = h->next;
    }
}

int main(){
    enqueue(1);
    enqueue(2);
    enqueue(3);

    print();

    dequeue();

    printf("\n");

    print();
}
```
