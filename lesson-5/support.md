This lesson's videos are broken up into two parts as functions are quite complicated.

<iframe width="560" height="315" src="https://www.youtube.com/embed/trTd2V8sjXY" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Key Takeaways
* A function is a block of code that performs a specific task.
* A function has 4 parts:
  * Type
  * Name
  * Inputs
  * Body
* Functions start off with a type, then function name, 2 parenthesis and then curly bracket. The content in the `()` will be the function arguments, which are newly declared variables. See below:
```
Type Name (...) {
  // body
}
```
* `main` is the first function that your C++ program you will always run.
* You can name functions whatever you want but for readability want to name the function that’s related to the body of the function.
* Functions should be named `UpperCamelCase`.
* `return` takes whatever value you provide and sets that as the value of your function.
* Once you return something, you will no longer be able to execute the rest of the function. It will terminate.

## Supplemental Information
### Function signature
Just like people have signatures for unique identification, so do functions. A functions signature includes everything but the body. So the signature for `main` is `int main()`. Using the function signature you should be able to quickly tell the type, name and inputs of a function. This is often what both humans and the computer use to indicate if the function is being used in a valid manner.


```cpp
int RectangleArea(int width, int height) {
  return width * height;
}
```
The signature here is `int RectangleArea(int width, int height)`. This means that the following are invalid usages of the `RectangleArea` function.
```cpp
RectangleArea(); // You need 2 parameters!
RectangleArea(10, 12, 23); // The signature indicates we only accept 2 parameters, not 3.
RectangleArea(10, "12"); // The second parameter is of int type, not string.
```

### Removing redundancy
One of the best usages of functions is to remove the redundancy of code. Lets take an example and see how a function might make it easier to interpret and modify.
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
  cout << "I'm going to list out numbers from 0 to 5" << endl;
  cout << "Number 0 is even" << endl;
  cout << "Number 1 is odd" << endl;
  cout << "Number 2 is even" << endl;
  cout << "Number 3 is odd" << endl;
  cout << "Number 4 is even" << endl;
  cout << "Number 5 is odd" << endl;
  return 0;
}
```

Now instead, recognize that this code could instead be written as:
```cpp
#include <iostream>
#include <string>
using namespace std;

bool IsEven(const int number) {
  string type = "";
  const is_even = (number % 2 == 0);
  if (is_even) {
    type = "even";
  } else {
    type = "odd";
  }
  cout << "Number " << number << " is " << type << endl;
  return is_even;
}

int main() {
  cout << "I'm going to list out numbers from 0 to 5" << endl;
  IsEven(0);
  IsEven(1);
  IsEven(2);
  IsEven(3);
  IsEven(4);
  IsEven(5);
  return 0;
}
```

This has a few benefits,
* If I wanted to change it from printing out `Number _ is __.` I could easily just change 1 line of code to make it instead print out `Value _ is __.` I
* To anyone reading the code, they can clearly see the same thing is happening to numbers 0-5 instead of guessing what what is going on.
* If there was a bug, I can isolate the bug to my function and fix there rather than fixing it 6 different times.
* Adding new numbers is very simple! As opposed to before where I would have to think about the correct value to print out.
