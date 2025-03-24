## Stack Data Structure

A **Stack** is a linear data structure that follows the **Last In, First Out (LIFO)** principle. This means that the last element added to the stack will be the first one to be removed.

## Operations of a Stack
1. **Push**: Add an element to the top of the stack.
2. **Pop**: Remove the element from the top of the stack.
3. **Top/Peek**: View the top element without removing it.
4. **IsEmpty**: Check if the stack is empty.
5. **IsFull**: Check if the stack is full (for array-based implementations).

### 1. **Array-based Stack (Static Stack)**
- A stack can be implemented using a static array.
- The stack has a fixed size, and elements are added or removed from the top of the stack using an index.

---

## Array-based Stack Implementation in C

Here is a basic implementation of a **stack using an array** in C:

```c
#include <stdio.h>
#include <stdlib.h>

#define MAX 5 // Maximum size of the stack

// Define the stack structure
struct Stack {
    int arr[MAX];
    int top;
};

// Initialize the stack
void initStack(struct Stack* stack) {
    stack->top = -1;
}

// Check if the stack is empty
int isEmpty(struct Stack* stack) {
    return stack->top == -1;
}

// Check if the stack is full
int isFull(struct Stack* stack) {
    return stack->top == MAX - 1;
}

// Push operation (add an element to the top of the stack)
void push(struct Stack* stack, int value) {
    if (isFull(stack)) {
        printf("Stack is full!\n");
        return;
    }
    stack->arr[++(stack->top)] = value;
    printf("%d pushed onto the stack\n", value);
}

// Pop operation (remove an element from the top of the stack)
int pop(struct Stack* stack) {
    if (isEmpty(stack)) {
        printf("Stack is empty!\n");
        return -1;
    }
    return stack->arr[(stack->top)--];
}

// Peek operation (view the top element of the stack without removing it)
int peek(struct Stack* stack) {
    if (isEmpty(stack)) {
        printf("Stack is empty!\n");
        return -1;
    }
    return stack->arr[stack->top];
}

// Display the stack
void displayStack(struct Stack* stack) {
    if (isEmpty(stack)) {
        printf("Stack is empty!\n");
        return;
    }
    printf("Stack elements: ");
    for (int i = 0; i <= stack->top; i++) {
        printf("%d ", stack->arr[i]);
    }
    printf("\n");
}

int main() {
    struct Stack stack;
    initStack(&stack);

    push(&stack, 10);
    push(&stack, 20);
    push(&stack, 30);

    displayStack(&stack);

    printf("%d popped from the stack\n", pop(&stack));

    displayStack(&stack);

    printf("Top element is: %d\n", peek(&stack));

    return 0;
}
```
