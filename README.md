# Data-Structure-Assignment

🔹 Q1: Reverse a String using Stack
 Concept

Stack (LIFO – Last In First Out)

 Algorithm
Start
Read the string
Push each character into stack
Pop characters one by one
Print popped characters (reversed string)
Stop

 Code:

#include <stdio.h>
#include <string.h>

#define MAX 100

char stack[MAX];
int top = -1;

void push(char ch) {
    stack[++top] = ch;
}

char pop() {
    return stack[top--];
}

int main() {
    char str[100];
    int i;

    printf("Enter string: ");
    scanf("%s", str);

    for(i = 0; i < strlen(str); i++) {
        push(str[i]);
    }

    printf("Reversed string: ");
    while(top != -1) {
        printf("%c", pop());
    }

    return 0;
}
Q2: Balanced Parentheses
 Concept

Stack

 Algorithm
Start
Read expression
Push '(' into stack
If ')' found → pop
If stack empty → balanced
Else → not balanced
Stop

 Code:


#include <stdio.h>
#include <string.h>

char stack[100];
int top = -1;

void push(char ch) {
    stack[++top] = ch;
}

void pop() {
    if(top != -1) top--;
}

int main() {
    char exp[100];
    int i;

    printf("Enter expression: ");
    scanf("%s", exp);

    for(i = 0; i < strlen(exp); i++) {
        if(exp[i] == '(')
            push('(');
        else if(exp[i] == ')') {
            if(top == -1) {
                printf("Not Balanced");
                return 0;
            }
            pop();
        }
    }

    if(top == -1)
        printf("Balanced Expression");
    else
        printf("Not Balanced");

    return 0;
}
Q3: Next Greater Element
 Concept

Array + Comparison Logic

 Algorithm
Start
Read array
Traverse array
Compare each element with next
Find next greater element
If none → print -1
Stop

code:

#include <stdio.h>

int main() {
    int arr[] = {4, 5, 2, 10, 8};
    int n = 5;
    int i, j, next;

    for(i = 0; i < n; i++) {
        next = -1;
        for(j = i + 1; j < n; j++) {
            if(arr[j] > arr[i]) {
                next = arr[j];
                break;
            }
        }
        printf("%d -> %d\n", arr[i], next);
    }

    return 0;
}

Q4: Printer Queue Simulation
 Concept

Queue (FIFO – First In First Out)

 Algorithm
Start
Create queue
Show menu
Insert document (enqueue)
Print document (dequeue)
Display queue
Stop

code:
#include <stdio.h>

#define MAX 5

int queue[MAX], front = -1, rear = -1;

void enqueue(int x) {
    if(rear == MAX - 1)
        printf("Queue Full\n");
    else {
        if(front == -1)
            front = 0;
        queue[++rear] = x;
    }
}

void dequeue() {
    if(front == -1)
        printf("Queue Empty\n");
    else {
        printf("Printed document: %d\n", queue[front]);
        front++;
        if(front > rear)
            front = rear = -1;
    }
}

void display() {
    int i;
    if(front == -1)
        printf("No documents\n");
    else {
        for(i = front; i <= rear; i++)
            printf("%d ", queue[i]);
    }
    printf("\n");
}

int main() {
    int ch, x;

    while(1) {
        printf("\n1.Add\n2.Print\n3.Display\n4.Exit\n");
        scanf("%d", &ch);

        switch(ch) {
            case 1:
                printf("Enter document id: ");
                scanf("%d", &x);
                enqueue(x);
                break;

            case 2:
                dequeue();
                break;

            case 3:
                display();
                break;

            case 4:
                return 0;
        }
    }
}

Q5: Circular Queue
 Concept

Circular Queue

 Algorithm
Start
Initialize queue
Enqueue using circular logic
Dequeue using circular logic
Display elements
Stop

 Code:

#include <stdio.h>

#define MAX 5

int queue[MAX], front = -1, rear = -1;

void enqueue(int x) {
    if((rear + 1) % MAX == front)
        printf("Queue Full\n");
    else {
        if(front == -1)
            front = 0;
        rear = (rear + 1) % MAX;
        queue[rear] = x;
    }
}

void dequeue() {
    if(front == -1)
        printf("Queue Empty\n");
    else {
        printf("Deleted: %d\n", queue[front]);
        if(front == rear)
            front = rear = -1;
        else
            front = (front + 1) % MAX;
    }
}

void display() {
    int i;

    if(front == -1)
        printf("Queue Empty\n");
    else {
        i = front;
        while(1) {
            printf("%d ", queue[i]);
            if(i == rear)
                break;
            i = (i + 1) % MAX;
        }
    }
    printf("\n");
}

int main() {
    int ch, x;

    while(1) {
        printf("\n1.Enqueue\n2.Dequeue\n3.Display\n4.Exit\n");
        scanf("%d", &ch);

        switch(ch) {
            case 1:
                printf("Enter value: ");
                scanf("%d", &x);
                enqueue(x);
                break;

            case 2:
                dequeue();
                break;

            case 3:
                display();
                break;

            case 4:
                return 0;
        }
    }
}


Learning Outcomes:
Understanding Stack and Queue operations
Implementing real-world problems
Strengthening C programming skills


Conclusion:

This project demonstrates how basic data structures like stacks and queues are implemented and used to solve practical problems efficiently.

