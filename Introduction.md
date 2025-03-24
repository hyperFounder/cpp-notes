### C++ Introduction: Loops, Function Pointers, Memory Allocation, Structs


### 1. Loops and Pointer arithmetic

```cpp
#include <iostream>
using namespace std;

int main() {
    // Array and for loop
    int arr[5] = {10, 20, 30, 40, 50};
    cout << "Array elements using for loop:" << endl;
    for (int i = 0; i < 5; ++i) {
        cout << "arr[" << i << "] = " << arr[i] << endl;
    }

    // Array and pointer arithmetic with for loop
    cout << "Array elements using pointer arithmetic:" << endl;
    for (int i = 0; i < 5; ++i) {
        cout << "*(arr + " << i << ") = " << *(arr + i) << endl;
    }

    // While loop with pointers
    int* ptr = arr;
    cout << "Array elements using pointer and while loop:" << endl;
    int count = 0;
    while (count < 5) {
        cout << "*ptr = " << *ptr << endl;
        ++ptr;
        ++count;
    }

    return 0;
}
```

### 2. Function Pointers

```cpp
#include <iostream>
using namespace std;

void greet() {
    cout << "Hello from greet!" << endl;
}

void customMessage(const string &msg) {
    cout << "Message: " << msg << endl;
}

int main() {
    // Function pointer to a function with no parameters
    void (*funcPtr1)() = &greet;
    funcPtr1();

    // Function pointer to a function with a parameter
    void (*funcPtr2)(const string &) = &customMessage;
    funcPtr2("Hello with a parameter!");

    return 0;
}

```



### 3. Dynamic Memory Allocation

- ```malloc``` and ```free``` in C corresponds to ```new``` and ```delete``` in C++

```cpp
#include <iostream>
#include <cstdlib> // For malloc and free
using namespace std;

int main() {
    // Allocate single integer dynamically using new
    int* p = new int(10);
    cout << "Value at p (new): " << *p << endl;
    delete p;

    // Allocate array dynamically using new
    int* arr = new int[5];
    for (int i = 0; i < 5; ++i) {
        arr[i] = i * 10;
    }
    for (int i = 0; i < 5; ++i) {
        cout << "arr[" << i << "] (new) = " << arr[i] << endl;
    }
    delete[] arr;

    // Allocate single integer dynamically using malloc
    int* q = (int*) malloc(sizeof(int));
    *q = 20;
    cout << "Value at q (malloc): " << *q << endl;
    free(q);

    // Allocate array dynamically using malloc
    int* arr2 = (int*) malloc(5 * sizeof(int));
    for (int i = 0; i < 5; ++i) {
        arr2[i] = i * 100;
    }
    for (int i = 0; i < 5; ++i) {
        cout << "arr2[" << i << "] (malloc) = " << arr2[i] << endl;
    }
    free(arr2);

    return 0;
}
```


### 4. Structs: Static vs Dynamic Objects

In C++, objects can be created either **statically** (on the stack) or **dynamically** (on the heap). Let's explore both approaches using structs.

---

#### Static Objects

Static objects are created on the stack. When you declare a static object, it is automatically destroyed when it goes out of scope.

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Person {
    string name;
    int age;

    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    // Static object (on the stack)
    Person p1 = {"Alice", 30};
    p1.display(); // Displays: Name: Alice, Age: 30

    // Static objects are automatically destroyed when they go out of scope
    return 0;
}
```
---
#### Dynamic Objects

Dynamic objects are created using new, which allocates memory on the heap. These objects must be explicitly deleted to free the memory.
```c++
#include <iostream>
#include <string>
using namespace std;

struct Person {
    string name;
    int age;

    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    // Dynamic object (on the heap)
    Person* p2 = new Person{"Bob", 25};
    p2->display(); // Displays: Name: Bob, Age: 25

    // Dynamically allocated objects must be explicitly deleted
    delete p2;  // Frees the memory

    return 0;
}
```
