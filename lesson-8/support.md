## Key Takeways
There are 2 techniques we can use to repeat code:
* while loops
* for loops

## Supplemental Information
### While Loops
Lets focus on `while` loops. Lets say we have the following code:
```cpp
void PrintNumbers() {
    cout << 1 << endl;
    cout << 2 << endl;
    cout << 3 << endl;
    cout << 4 << endl;
    cout << 5 << endl;
}
```
Using a `while` loop we could write the same code as:
```cpp
void PrintNumbers() {
    int number = 1;
    while (number <= 5) {
        cout << number << endl;
        number++;
    }
}
```
The `while` loop has almost the same structure as an `if` statement.
```cpp
while(expr) {
    // body
}
```
The only difference is that unlike an `if` statement which simply either executes the body or skips the body, the `while` statement continuously executes the body as long as `expr` is true. In the `PrintNumbers` example, we would excute the body of the code 5 times.
1. when `number == 1` since `1 <= 5` is true.
1. when `number == 2` since `2 <= 5` is true.
1. when `number == 3` since `3 <= 5` is true.
1. when `number == 4` since `4 <= 5` is true.
1. when `number == 5` since `5 <= 5` is true.
1. when `number == 6`, we skip to after the `while` loop since `6 <= 5` is false.

Go ahead, try and walk through `PrintNumbers` in a memory table and see what happens.

#### Variable Termination
The convinient thing about loops is they enable you to do something you haven't been able to do yet: Execute code a varible number of times. Lets say the goal of the program is to ask the user for input. Then print out all numbers less than that number starting from 1. Without loops that seems like an impossible task! However with one quick modification to our `PrintNumbers` function, it becomes easy!

```cpp
void PrintNumbers(int limit) {
    int number = 1;
    while (number < limit) {
        cout << number << endl;
        number++;
    }
}
```

By changing the condition of the `while` from `number <= 5` to `number < limit`, we allow the code to execute as many times as the condition is true. Go ahead, try and use this code with various inputs in a REPL to get used to it.

#### Infinite Loops
One of the most common bug encountered with loops will be infite loops. An infite loops is when your loop never has a termination clause. For example:
```cpp
while(true) {
    cout << "Hi!" << endl;
}
cout << "Lets Start!" << endl;
```
Can you spot why this is an infinite loop?
<details><summary>Answer</summary>This code would never print <code>Lets Start!</code> as the <code>while</code> loop expression would always be true and hence always execute the body.
</details><br />
