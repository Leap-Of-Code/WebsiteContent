## Supplemental Information
Sorry! No video for this lesson :(

Today we'll be focusing on a few key concepts to make our code easier to read and better understand functions.
1. [Functions that don't return anything](#functions-that-don't-return-anything)
3. [Else statements](#else-statements)
4. [Increment and Decrement operators](#increment-and-decrement-operators)
5. [Documenting a function](#documenting-a-function)

### Functions that don't return anything
Remember a function has 4 things it needs.
  * Return type
  * Name
  * Arguements (and these can be empty!)
  * Body

Whenever you have a function that doesn't return anything, you can simply denote that with a return type of `void`. The `void` keyword assures that the function will have no value. That also means you can't assign from a void function. For example,

```cpp
int Foo() {
    return 6;
}

void Bar(int some_number) {
    if (some_number < 10) {
        return; // I can still use the return keyword to exit the function early,
                // however it won't set a value as a void function as no value.
    }

    cout << "Number is more than 9!" << endl;
    // Do some more stuff here...
    return;
}

int main() {
    int foo_var = Foo(); // This is valid.
    int bar_var = Bar(foo_var); // This is invalid no matter what the type of bar_var
                                // is as Bar() is a void function that doesn't return
                                // anything!
}
```

Try running that code in a repl and seeing the error you get. The correct code here is below:

```cpp
int Foo() {
    return 6;
}

void Bar(int some_number) {
    if (some_number < 10) {
        return; // I can still use the return keyword to exit the function early,
                // however it won't set a value as a void function as no value.
    }

    cout << "Number is more than 9!" << endl;
    // Do some more stuff here...
    return;
}

int main() {
    int foo_var = Foo(); // This is valid.
    Bar(foo_var); // This is valid, as Bar() doesn't return any value I wasn't
                  // allowed to assign from it earlier.
}
```

### Else statements
Up until now you may be wondering how to write a conditional where you do either one thing or another. One option to do do this would be:
```cpp
int main() {
    bool my_bool = /*either true or false*/;
    if (my_bool) {
        // Code Block A.
    }
    if (!my_bool) {
        // Code Block B.
    }
}
```
Depending on the value of `my_bool` either `Code Block A` will execute or `Code Block B`, but not both. By using the `else` keyword we can simplify the code above to:
```cpp
int main() {
    bool my_bool = /*either true or false*/;
    if (my_bool) {
        // Code Block A.
    } else {
        // Code Block B.
    }
}
```
This code says, if `my_bool` is <code style="color:blue"><b>true</b></code>, execute `Code Block A` otherwise if `my_bool` is <code style="color:red"><b>false</b></code>, execute `Code Block B`. The benefit of writing code this way is that to anyone that reads the code, the following is clear:
1. One of Code Block A and B will definetly happen as `my_bool` will always be either <code style="color:blue"><b>true</b></code> or <code style="color:red"><b>false</b></code>.
2. Code Block A and B can not both happen in one execution of the code as they are in different `if` `else` blocks.

Lets say you had the following code:
```cpp
int main() {
    int my_value = /*some number*/;
    if (my_value < 10) {
        // Code Block A
    }
    if (10 <= my_value && my_value < 20) {
        // Code Block B
    }
    if (20 <= my_value) {
        // Code Block C
    }
}
```
This code only enables one of Code Block A, B, or C to occur. If `my_value` is less than 10, A happens. If `my_value` is between 10 and 20, B happens. If `my_value` is greater than or equal to 20, C happens. Take some time to make sure you understand the code above before moving forward.

Because there are three cases here, we can't just use an `else` to simplify our code since an `else` only allows for either of two things to happen. Instead we'll use a new concept.
```cpp
int main() {
    int my_value = /*some number*/;
    if (my_value < 10) {
        // Code Block A
    } else if (my_value < 20) {
        // Code Block B
    } else {
        // Code Block C
    }
}
```
Note this code is doing exactly the same as the code above.
* If `my_value` is less than 10, Code Block A happens.
* Otherwise we move on to check if `my_value` is less than 20. If so, Code Block B happens. Note, we are only checking `my_value < 20` if and only if `my_value` is not less than 10.
* If `my_value` is not less than 20, then finally we do Code Block C as its the final else clause.

Notice, only one of Code Block A, B, or C will occur, but because here we've structured our code using connected `if` `else if` `else` blocks, its much more clear that only one of A, B, or C can occur as opposed to the example above where we only use `if`.

With every `if` block, you can chain as many `else if` statements as you'd like, and then you can optionally terminate it with an `else` statement.

### Increment and Decrement operators
By now, you might have written code such as `i = i + 5;` or `i = i - 7;`. A shorthand way to represent all of that is `i += 5;` or `i -= 7;` respectively.
Similarly you can do the same with `*` or `/` by doing `i *= 52;` or `i /= 2;`. For the case of adding 1 or subtracting 1, we actually have even more short hand terms.

| Basic Form | Simplified Form | Simplest form |
| - | - | - |
| `i = i + 5` | `i += 5` |  |
| `i = i - 7` | `i -= 7` |  |
| `i = i + 1` | `i += 1` | `i++` |
| `i = i - 1` | `i -= 1` | `i--` |

### Documenting a function
The best thing you can do for anyone reading the code (that mostly refers to your future self), is documenting your code appropriately. Lets say you have the following two function:
```cpp
int Foo(float a, float b, float c) {
    // Does something.
}

float Bar(float a, float b, float c) {
    // Does something.
}
```
I could make this code significantly more clear by doing the following:
```cpp
/* Evaluates the type of triangle.
 * Args:
 *   leg0: First leg of the triangle.
 *   leg1: Second leg of the triangle.
 *   leg2: Third leg of the triangle.
 * Returns:
 *   -1: Invalid triangle
 *    0: Equilateral triangle
 *    1: Isosceles triangle
 *    2: Scalene triangle
 */
int TriangleType(float leg0, float leg1, float leg2) {
    // Does something.
}

/* Computes the area of the triangle.
 * Args:
 *   leg0: First leg of the triangle.
 *   leg1: Second leg of the triangle.
 *   leg2: Third leg of the triangle.
 * Returns:
 *   float: The area.
 */
float TriangleArea(float leg0, float leg1, float leg2) {
    // Does something.
}
```
Now someone could understand what this function does and how to use it without having to read the body of the function. That's what you should strive for! Notice I improved the code by both using better names for the functions and arguements and also by adding comments.
