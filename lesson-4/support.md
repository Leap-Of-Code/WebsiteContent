## Key Takeaways
* Scope helps define the lifetime of a variable. We use curly brackets `{}` to show beginning and end of a scope.
* Your code can have multiple scopes. In the memory table, we display the start of a scope with a star.
* `if` blocks enable our code to make decisions. They are the first of a group of concepts called conditionals.

## Supplemental Information
### Arbitrary scope
You can include scope wherever you like. You don't **need** an `if` block. It can enable you to do things such as have multiple variables of the same name. For example this is valid code.
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
  {
    int first_variable = 10;
    cout << "first_variable is: " << first_variable << endl;
  }
  int first_variable = 15;
  cout << "first_variable is: " << first_variable << endl;
}
```
and will produce
```
first_variable is: 10
first_variable is: 15
```
The first time `first_variable` is declared, it will go out of scope two lines after. Then a **new** `first_variable` will be declared, which will go out of scope at the end of the program.
