## Key Takeways
`For` loops and `while` loops perform virtually the same task. The main difference of which to use when really comes down to semantics. Anything you can do with a `for` loop, you can do with a `while` loop. Anything you can do with a `while` loop, you can do with a `for` loop. Typically, most people use a `while` loop when you aren't sure when to end the loop.

## Supplemental Information
Sorry! No video for this lesson :(
### For Loops
The `for` loop looks like the following:
```cpp
for (int x = 0; x < 10; x+=1) {
    // body
}
```
Take note of the **semicolons** that break down the 3 parts of the for loop.
1. `int x = 0` : **Loop initialization**. Here, you define the variable used in the loop. Note, a variable defined here is only defined in the scope of the `for` loop. It's not available after the `for` loop terminates.
2. `x < 10` : **Terminal Condition**. Like the `while` and `if`, this is the condition you want to stop the `for` loop at. This is checked everytime before the body is executed.
3. `x+=1` : **Increment**. At the bottom of a `while` loop you would increment the loop variable. The `for` expression formalizes it as a part of the definition so you don't accidentlly skip it.

The `for` above is exactly the same as the `while` code below:
```cpp
int x = 0;
while(x < 10) {
    // body
    x++;
}
```

Notice, while both of those code segements are doing the same thing there is 1 major difference. The variable `x` goes out of scope in the `for` loop, but in the `while`, it is available after the `while` has terminated.

### Using for vs while
One of the most common examples for using a `while` loop is when the terminating condition is based on a user input. Take a look at this code:
```cpp
int Guess() {
    cout << "Enter a guess: ";
    int number;
    cin >> number;
    return number;
}

int main() {
    int magic_number = 15;
    int guess = Guess();
    while (guess != magic_number) {
        cout << "Try again! ";
        guess = Guess();
    }
    cout << "That's it!" << endl;
    return 0;
}
```

<details><summary>What is the the maximum number of times the Guess function be called?</summary>You can't actually know! What if the user always enters the exact same guess every single time?</details><br />

With `for` loops, its good practice to use them when you know what the start and end conditions are and exactly how many times you will go through the loop.
```cpp
void PrintBox(int size) {
    for (int i=0; i < size; i++) {
        char horizontal = ' ';
        char vertical = '|';

        if (i == 0 || i == size - 1) {
            horizontal = '_';
        }

        if (i == 0) {
            vertical = ' ';
        }

        cout << vertical;
        for (int j=0; j < size; j++) {
            cout << horizontal;
        }
        cout << vertical << endl;
    }
}
```
Written with `while`, the same code is:
```cpp
void PrintBox(int size) {
    int i = 0;
    while (i < size) {
        char horizontal = ' ';
        char vertical = '|';

        if (i == 0 || i == size - 1) {
            horizontal = '_';
        }

        if (i == 0) {
            vertical = ' ';
        }

        cout << vertical;
        int j = 0;
        while (j < size) {
            cout << horizontal;
            j++;
        }
        cout << vertical << endl;

        i++;
    }
}
```
Personally, I find the `for` statement to be much better to read and it keeps the scope of both the `i` and `j` variable to only the `for` loop! Do you agree?

### Infinite For Loops
Remeber how the following code never terminates?
```cpp
int counter = 0;
while(true) {
    cout << counter << endl;
    counter++;
}
```
We could write the same code in our `for` loop:
```cpp
for (int counter = 0; ; counter++) {
    cout << counter << endl;
}
```
While this is valid code, this is **NOT** good code! If you don't want a termination condition, consider using the `while` code above. Similarly, you can remove any of the 3 parts of the `for` loop and the code will still compile as long as you have the 2 semicolons.
