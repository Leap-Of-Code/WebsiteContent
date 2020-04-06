## Key Takeaways
* Memory tables consist of `type`, `name` of the variable, and `value` of the variable in 3 separate columns
* Memory tables are sequential. If you mess up on memory table, start over again, from the beginning.
* The memory table always begins at `main`!
* No matter what line of code we are on, we can only use the variables that are already in the memory table.

## Supplemental Information
### Debugging
Debugging is the process of identifying and removing errors from computer hardware or software. Your memory table is the primary tool for determining issues. If your code runs, then you should **always** be able to understand what the issue is by running it through your memory table.

### Variables without assignment
Its possible to create a variable without assigning to it. In that case the value of the variable is unknown. We represent this using a `?` in our memory table.
For example:
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    int x;
    cout << "The initial value of X is: " << x << endl;
    x = 100;
    cout << "The final value of X is: " << x << endl;

    return 0;
}
```

There's no gaurantee what the initial value of X is. It might be 0, it might be 1234, or any other number. Hence why we refer to it as a `?` in our memory table when we create the variable using `int x;`. If we had done `int x = 100;` Then we would have created it with the value of `100` assigned to it. Its perfectly valid to have a variable not have an initial value if you'll be filling it in later either from user input or another function.

BUT, if you ever find you are reading from a value that is a `?` in your memory table, you probably have a bug in your code!
