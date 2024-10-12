# Queue using array

Experiment 19

## Aim 
To study and implement Queue implementation using array.

## Theory

A **Queue** is a linear data structure that follows the **FIFO (First In First Out)** principle. In a queue, the first element that is added will be the first one to be removed, just like a line of people waiting in a queue.

### Key Points:
- **Front**: The position of the first element in the queue.
- **Rear**: The position where the next element will be added.
- **Capacity**: The maximum number of elements the queue can hold.
- **Operations**:
  - **Enqueue (push)**: Add an element to the end of the queue (at the rear).
  - **Dequeue (pop)**: Remove the front element from the queue.
  - **Peek**: Access the front element without removing it.

### Example:
Let’s assume we have a queue with a capacity of 5, and we enqueue elements 10, 20, and 30:


## Code

```cpp
#include <iostream>
using namespace std;

class Queue {
public:
    int capacity;
    int front;
    int rear;
    int* arr;

    // Constructor to initialize the queue
    Queue(int capacity) {
        this->capacity = capacity;
        arr = new int[capacity];
        front = -1; // Set front to -1 indicating an empty queue
        rear = -1;  // Set rear to -1 indicating an empty queue
    }

    // Enqueue: Add an element to the queue
    void push(int element) {
        if (rear + 1 < capacity) { // Check if there's space in the queue
            if (front == -1) { // If queue is empty
                front = 0;     // Initialize front
            }
            rear++;
            arr[rear] = element;
        } else {
            cout << "Queue Overflow" << endl;
        }
    }

    // Dequeue: Remove an element from the queue
    void pop() {
        if (front >= 0) {
            // If there's only one element, reset front and rear
            if (front == rear) {
                front = rear = -1; // Reset to indicate queue is empty
            } else {
                front++;
            }
        } else {
            cout << "Queue Underflow" << endl;
        }
    }

    // Peek: Get the front element of the queue
    int peek() {
        if (front >= 0) {
            return arr[front];
        } else {
            return -1; // Indicate that the queue is empty
        }
    }

    // Destructor to free allocated memory
    ~Queue() {
        delete[] arr;
    }
};

int main() {
    Queue q(5); // Initialize queue with a capacity of 5
    q.push(10);
    q.push(20);
    q.push(30);

    cout << "Front element: " << q.peek() << endl; // Should print 10

    q.pop(); // Remove 10
    cout << "Front element after pop: " << q.peek() << endl; // Should print 20

    return 0;
}
```


## Algorithm

1. **Start**
2. Create a class `Queue` with:
   - An integer variable `capacity` to hold the maximum size.
   - Two integer variables `front` and `rear` initialized to -1 (indicating an empty queue).
   - A dynamic array `arr` to store the elements.
3. Define a function `push(int element)` to add elements to the queue:
   - If the queue is not full (`rear + 1 < capacity`), increment `rear` and assign the element to `arr[rear]`.
   - If the queue was empty (`front == -1`), set `front = 0` to point to the first element.
   - If the queue is full, print "Queue Overflow".
4. Define a function `pop()` to remove the front element:
   - If the queue is not empty (`front >= 0`), increment `front` to remove the element.
   - If there’s only one element, reset both `front` and `rear` to -1 to indicate the queue is empty.
   - If the queue is empty, print "Queue Underflow".
5. Define a function `peek()` to return the front element:
   - If the queue is not empty, return the element at `arr[front]`.
   - Otherwise, return -1 to indicate the queue is empty.
6. In the `main()` function:
   - Initialize the queue with a capacity of 5.
   - Enqueue elements 10, 20, and 30.
   - Print the front element using `peek()`.
   - Dequeue the front element and print the new front element using `peek()`.
7. **End**
