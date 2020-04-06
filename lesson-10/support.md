## Great work so far!
Firstly, take a congragulatory moment for yourself. You did it! You've completed the basic concepts of programing. C++ only has a total of 58 key words. Up until now, we've covered 22 of them! That's **37%**! Not only that, these 22 key words make up the basis of almost all programming languages. Everything we do from here on out, are concepts that heavily reuse these words.

| | | |
|-|-|-|
bool | int | void |
char | long | while |
string | return | && (and) |
else | short | \|\| (or) |
false | signed | ^ (xor) |
float | sizeof | ! (not) |
for | true |  |
if | unsigned | |


As a quick review, take a few minutes to go over the list and make sure you rememember them all. If not check out the previous lessons to brush up!

And now back to buisness...

## Supplemental Information
### Structs
Structs are a way of grouping types together in C++. Just like functions, structs don't change what your code does, they simply make it easier for you and anyone else to interpret your code. To help better understand that, this lesson will be organized with a follow along exercise in mind. Take time to implement the solution to every question on your own. The answers will be available, but look at them **only after** you've implemented it on your own, on paper.

#### Part 0
```
Write code to take in a fraction from a user and print it out.
Do not use decimals to represent the fraction, use only whole numbers.
```

<details><summary>Hint</summary>What are the parts of a fraction?
<details><summary>Hint</summary>What is the type of the numerator and denominator?
<details><summary>Hint</summary>
A fraction is written out like: <code>1/2</code>.
</details></details></details>

<details><summary>Solution</summary><details><summary>Are you sure you want to see the answer?</summary>

```cpp
#include <iostream>

int GetUserInput() {
    int number;
    std::cin >> number;
    return number;
}

void PrintFraction(int numerator, int denominator) {
    std::cout << numberator << '/' << denominator;
}

int main() {
    std::cout << "Enter the numerator: ";
    int numerator = GetUserInput();
    std::cout << "Enter the denominator: ";
    int denominator = GetUserInput();

    PrintFraction(numerator, denominator);
    return 0;
}
```
</details></details><br />

#### Part 1
```
Write code to reduce a fraction to it's simplest form.
9/18 -> 1/2
1/2  -> 1/2
```

<details><summary>Hint</summary>How do you reduce a fraction?
<details><summary>Hint</summary>How can the Greatest Common Factor help?
<details><summary>Hint</summary>The Greatest Common Factor of 9 and 18 is 9. 9/18 is (9 / 9)/(18 / 2)</details></details></details>

<details><summary>Solution</summary><details><summary>Are you sure you want to see the answer?</summary>

```cpp
#include <iostream>

int GetUserInput() {
    int number;
    std::cin >> number;
    return number;
}

void PrintFraction(int numerator, int denominator) {
    std::cout << numberator << '/' << denominator;
}

int GreatestCommonFactor(int num1, int num2) {
    for (int i = num1; i > 1; i--) {
        if ((num1 % i == 0) && (num2 % i == 0)) {
            return i;
        }
    }
    return 1;
}

int main() {
    std::cout << "Enter the numerator: ";
    int numerator = GetUserInput();
    std::cout << "Enter the denominator: ";
    int denominator = GetUserInput();
    std::cout << "Input: ";
    PrintFraction(numerator, denominator);
    std::cout << std::endl;


    int gcf = GreatestCommonFactor(numerator, denominator);
    numerator /= gcf;
    denominator /= gcf;
    std::cout << "Simplified: ";
    PrintFraction(numerator, denominator);
    std::cout << std::endl;

    return 0;
}
```
</details></details><br />

#### Part 2
Now you might have realized its not possible to create a function of the sorts `SimplifyFraction` as then you would somehow have to return both the numerator and denominator. And as we know, we can't return multiple variables from one function. At least not until now! This is where `struct` comes into play. A `struct` lets you group up multiple types together to make a new type of your own. The syntax looks like the following:
```cpp
struct MyTypeName {
    // struct members
};
```

The keyword `struct` is used to indicate that you're making a new type.
`MyTypeName` is the name of your new type. This of this as another option now available to you just like `int`, `char`, or `float`.
And the `;` represents the end of the definition.
In the `struct` members, you can add a type and name of all the **members** you'd like to struct to contain.  For example:

```cpp
struct Student {
    char first_initial;
    char last_initial;
    int grade;
};
```

In this case, my `Student` type has 3 members: `first_initial`, `last_initial`, and `grade`. To create a `Student` variable the following code would work:

```cpp
struct Student {
    char first_initial;
    char last_initial;
    int grade;
};

int main() {
    Student s;
    s.first_initial = 'V';
    s.last_initial = 'G';
    s.grade = 75;
}
```

Notice I can use the `.` symbol to access the members of the `s` variable which is of type `Student`. Now lets write a function to print out a `Student` type. We can't use `std::cout << s;` anymore because `std::cout` only knows how to print what are called **primitive types**. These are the types that already exist (refer to lesson03 for a complete list). For all custom types you'll have to write your own function.
```cpp
void Print(Student a) {
    std::cout << a.first_initial << '.' << a.last_initial << ". :: " << a.grade;
}
```
I could have made this function do anything I want with the members. For example, the following is just as good, it all depends on what I want the code to print out as.

```cpp
void Print(Student a) {
    std::cout << "First: " << a.first_initial << std::endl
              << "Last: " << a.last_initial << std::endl
              << "Grade: " << a.grade;
}
```

Using the `Print` function is exactly the same for the `Student` type as it is for `int`s or any other type.
```cpp
#include <iostream>

struct Student {
    char first_initial;
    char last_initial;
    int grade;
};

void Print(Student a) {
    std::cout << "First: " << a.first_initial << std::endl
              << "Last: " << a.last_initial << std::endl
              << "Grade: " << a.grade;
}

int main() {
    Student s;
    s.first_initial = 'V';
    s.last_initial = 'G';
    s.grade = 75;
    Print(s);
}
```

Similarly you can always return a `Student` type from a function as well.
```cpp
#include <iostream>

struct Student {
    char first_initial;
    char last_initial;
    int grade;
};

Student CreateStudent() {
    Student s;
    std::cout << "First Initial: ";
    std::cin >> s.first_initial;
    std::cout << "Last Initial: ";
    std::cin >> s.last_initial;
    std::cout << "Grade: ";
    std::cin >> s.grade;
    return s;
}

int main() {
    Student s = CreateStudent();
}
```

And last, as with every variable, a `struct` type will always have a size as well. The size of a `struct` will be a sum of all the sizes of its members. So `Student` type has a size of `sizeof(char) + sizeof(char) + sizeof(int) = 1 + 1 + 4 = 6` bytes.

Now the task for you is
```
Create a struct to represent a fraction.
Write code to do Part 0 and 1 using this new struct.
```

<details><summary>Solution</summary><details><summary>Are you sure you want to see the answer?</summary>

```cpp
#include <iostream>

struct Fraction {
    int numerator;
    int denominator;
};

Fraction GetUserInput() {
    Fraction val;
    std::cout << "Enter the numerator: ";
    std::cin >> val.numerator;
    std::cout << "Enter the denominator: ";
    std::cin >> val.denominator;
    return val;
}

void PrintFraction(Fraction value) {
    std::cout << value.numberator << '/' << value.denominator;
}

int GreatestCommonFactor(int num1, int num2) {
    for (int i = num1; i > 1; i--) {
        if ((num1 % i == 0) && (num2 % i == 0)) {
            return i;
        }
    }
    return 1;
}

Fraction Simplify(Fraction value) {
    int gcf = GreatestCommonFactor(value.numerator, value.denominator);
    Fraction result;
    result.numerator = value.numerator / gcf;
    result.denominator = value.denominator / gcf;
    return result;
}

int main() {
    Fraction value = GetUserInput();
    PrintFraction(value);
    std::cout << std::endl;

    std::cout << "Simplified: ";
    value = Simplify(value);
    PrintFraction(value);
    std::cout << std::endl;

    return 0;
}
```
</details></details><br />

#### Part 3
* A `struct` can have 1 member.
* The types of members in `struct`s can be other `struct`s.

```cpp
struct Foo {
    char a;
};

struct Bar {
    Foo f;
    int b;
};

int main() {
    Bar bar;
    bar.b = 10;
    bar.f.a = 'a';
}
```
* Remember, the `sizeof` function can be used to determine the size of any variable or type. `sizeof(Foo)` would return `1`.
