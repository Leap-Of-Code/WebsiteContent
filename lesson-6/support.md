## Supplemental Information
Sorry! No video for this lesson :(

### Boolean operators
Just like you are able to operate on `int`s with multiplication, addition, subtraction, division, and modulo, you can also operate on booleans. These are called boolean operators. The boolean operators are:
  * not `!`
  * and `&&`
  * or `||`
  * xor `^`

For each of the operators, you can both read the summary of how it works and see what it's result will be by using the truth tables below.

`not A` or `!A` is <code style="color:blue"><b>true</b></code> if A is <code style="color:red"><b>false</b></code>, and vice versa.

| A | `!A` |
| - | ------ |
| <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> |
| <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> |

`A and B` or `A && B` is <code style="color:blue"><b>true</b></code> whenever both A and B are <code style="color:blue"><b>true</b></code>, otherwise its <code style="color:red"><b>false</b></code>.

| A | | B | | `A && B` |
| - | - | - | - | ------ |
| <code style="color:blue"><b>true</b></code> | && | <code style="color:blue"><b>true</b></code> | = | <code style="color:blue"><b>true</b></code> |
| <code style="color:blue"><b>true</b></code> | && | <code style="color:red"><b>false</b></code> | = | <code style="color:red"><b>false</b></code> |
| <code style="color:red"><b>false</b></code> | && | <code style="color:blue"><b>true</b></code> | = | <code style="color:red"><b>false</b></code> |
| <code style="color:red"><b>false</b></code> | && | <code style="color:red"><b>false</b></code> | = | <code style="color:red"><b>false</b></code> |

`A or B` or `A || B` is <code style="color:blue"><b>true</b></code> whenever any of A or B are <code style="color:blue"><b>true</b></code>, otherwise its <code style="color:red"><b>false</b></code>.

| A | | B | | `A \|\| B` |
| - | - | - | - | ------ |
| <code style="color:blue"><b>true</b></code> | \|\| | <code style="color:blue"><b>true</b></code> | = | <code style="color:blue"><b>true</b></code> |
| <code style="color:blue"><b>true</b></code> | \|\| | <code style="color:red"><b>false</b></code> | = | <code style="color:blue"><b>true</b></code> |
| <code style="color:red"><b>false</b></code> | \|\| | <code style="color:blue"><b>true</b></code> | = | <code style="color:blue"><b>true</b></code> |
| <code style="color:red"><b>false</b></code> | \|\| | <code style="color:red"><b>false</b></code> | = | <code style="color:red"><b>false</b></code> |

`A xor B` or `A ^ B` is <code style="color:blue"><b>true</b></code> whenever only one of A or B are <code style="color:blue"><b>true</b></code>, otherwise its <code style="color:red"><b>false</b></code>. xor is short for exclusive-or.

| A | | B | | `A ^ B` |
| - |- | - | - | ------ |
| <code style="color:blue"><b>true</b></code> | ^ | <code style="color:blue"><b>true</b></code> | = | <code style="color:red"><b>false</b></code> |
| <code style="color:blue"><b>true</b></code> | ^ | <code style="color:red"><b>false</b></code> | = | <code style="color:blue"><b>true</b></code> |
| <code style="color:red"><b>false</b></code> | ^ | <code style="color:blue"><b>true</b></code> | = | <code style="color:blue"><b>true</b></code> |
| <code style="color:red"><b>false</b></code> | ^ | <code style="color:red"><b>false</b></code> | = | <code style="color:red"><b>false</b></code> |

### Use cases
Often you'll be using boolean operators to express what you want your code to do. For example you may have the following problem assigned to you.

```
Ask the user for a number.
If it divides evenly by both 3 and 5, print "DONG!".
Otherwise, if the number divides evenly by 3, print "Tick".
Otherwise, if the number divides evenly by 5, print "Tock".
In all other cases print out the number.
```

```cpp
int main() {
    // Asking the user for a number.
    int number = GetUserInput();

    // Using variables to get the divisbility of the number.
    bool divides_by_3 = (number % 3 == 0); // True if number evenly divides 3.
    bool divides_by_5 = (number % 5 == 0); // True if number evenly divides 5.

    // If the number divides by 3 AND 5.
    if (divides_by_3 && divides_by_5) {
        cout << "DONG!";
    }

    // If the number divides only by 3 (but doesn't divide by 5).
    if (divides_by_3 && !divides_by_5) {
        cout << "Tick";
    }

    // If the number divides only by 5 (but doesn't divide by 3).
    if (divides_by_5 && !divides_by_3) {
        cout << "Tock";
    }

    // If a number doesn't divide by 3 and 5.
    if (!divides_by_3 && !divides_by_5) {
        cout << number;
    }

    return 0;
}
```

This is how you read each of the `if` clauses.
```cpp
    // If divides_by_3 is true AND divides_by_5 is true, then execute the block.
    // This will trigger only when both divides_by_3 and divides_by_5 are true.
    if (divides_by_3 && divides_by_5)
```
```cpp
    // If divides_by_3 is true AND NOT (divides_by_5 is true), then execute the block.
    // This will trigger only when divides_by_3 is true and divides_by_5 is false.
    if (divides_by_3 && !divides_by_5)
```
```cpp
    // If divides_by_5 is true AND NOT (divides_by_3 is true), then execute the block.
    // This will trigger only when divides_by_3 is false and divides_by_5 is true.
    if (divides_by_5 && !divides_by_3)
```
```cpp
    // If NOT (divides_by_3 is true) AND NOT (divides_by_5 is true), then execute the block.
    // This will trigger only when both divides_by_3 and divides_by_5 are false.
    if (!divides_by_3 && !divides_by_5))
```

### De Morgan's Law
One important concept to grasp regarding boolean operators is that you can combine values in different ways and still get the same result.
De Morgan's Law specifically states:
 1. `!(a && b)` is the same as `(!a || !b)`.
 2. `!(a || b)` is the same as `(!a && !b)`.
Notice that De Morgan's Law gives us a way to swap ORs `||` with ANDs `&&` and vice versa.

#### Creating Truth Tables
```cpp
bool var_a = /*either true or false*/;
bool var_b = /*either true or false*/;

// option_0 = NOT (var_a OR var_b)
bool option_0 = !(var_a || var_b);
// option_1 = (NOT var_a) AND (NOT var_b)
bool option_1 = ((!var_a) && (!var_b));
```
Let's start by building a truth table. We have 2 inputs - `var_a` and `var_b` - and 2 outputs - `option_0` and `option_1`.

| var_a | var_b | option_0 <br />`!(var_a \|\| var_b)` | option_1 <br>`((!var_a) && (!var_b))`|
| -| - | - | - |
| | | | |

We know `var_a` can be either <code style="color:blue"><b>true</b></code> or <code style="color:red"><b>false</b></code> so lets fill that in.

| var_a | var_b | option_0 <br />`!(var_a \|\| var_b)` | option_1 <br>`((!var_a) && (!var_b))`|
| -| - | - | - |
| <code style="color:blue"><b>true</b></code> | | | |
| <code style="color:red"><b>false</b></code> | | | |

We also know `var_b` can be either <code style="color:blue"><b>true</b></code> or <code style="color:red"><b>false</b></code>, however this is the case for all possibilities of `var_a`. This is shown using this table.

| var_a | var_b | option_0 <br />`!(var_a \|\| var_b)` | option_1 <br>`((!var_a) && (!var_b))`|
| -| - | - | - |
| <code style="color:blue"><b>true</b></code> | <code style="color:blue"><b>true</b></code> | | |
| <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> | | |
| <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> | | |
| <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> | | |

Now we just fill in the values for our outputs `options_0` at first.

| var_a | var_b | option_0 <br />`!(var_a \|\| var_b)` | option_1 <br>`((!var_a) && (!var_b))`|
| -| - | - | - |
| <code style="color:blue"><b>true</b></code> | <code style="color:blue"><b>true</b></code> | <code>!(<span style="color:blue"><b>true</b></span> \|\| <span style="color:blue"><b>true</b></span>)</code> | |
| <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> | <code>!(<span style="color:blue"><b>true</b></span> \|\| <span style="color:red"><b>false</b></span>)</code> | |
| <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> | <code>!(<span style="color:red"><b>false</b></span> \|\| <span style="color:blue"><b>true</b></span>)</code> | |
| <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> | <code>!(<span style="color:red"><b>false</b></span> \|\| <span style="color:red"><b>false</b></span>)</code> | |

Simplifing inside the `( )` we get:

| var_a | var_b | option_0 <br />`!(var_a \|\| var_b)` | option_1 <br>`((!var_a) && (!var_b))`|
| -| - | - | - |
| <code style="color:blue"><b>true</b></code> | <code style="color:blue"><b>true</b></code> | <code>!(<span style="color:blue"><b>true</b></span>)</code> | |
| <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> | <code>!(<span style="color:blue"><b>true</b></span>)</code> | |
| <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> | <code>!(<span style="color:blue"><b>true</b></span>)</code> | |
| <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> | <code>!(<span style="color:red"><b>false</b></span>)</code> | |

Simplifying again we get:

| var_a | var_b | option_0 <br/>`!(var_a \|\| var_b)` | option_1 <br/>`((!var_a) && (!var_b))`|
| -| - | - | - |
| <code style="color:blue"><b>true</b></code> | <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> | |
| <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> | |
| <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> | |
| <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> | |

If you follow a similar process for `option_1`, you will get the final table:

| var_a | var_b | option_0 <br/>`!(var_a \|\| var_b)` | option_1 <br/>`((!var_a) && (!var_b))`|
| -| - | - | - |
| <code style="color:blue"><b>true</b></code> | <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> |
| <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> |
| <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> |
| <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> | <code style="color:blue"><b>true</b></code> |

How are they the same? De Morgan's Law!

### Truth Tables to Boolean statements

Let's say you had the truth table and were tasked with finding the boolean statement for `result` in terms of `var_a` `var_b` and `var_c`.

| var_a | var_b | var_c | result |
| -| - | - | - |
| <code style="color:blue"><b>true</b></code> | <code style="color:blue"><b>true</b></code> | <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> |
| <code style="color:blue"><b>true</b></code> | <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> |
| <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> |
| <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> |
| <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> | <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> |
| <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> |
| <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> |
| <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> |

One way to approach this would be to find all the cases where `result` is <code style="color:blue"><b>true</b></code> (2 in this case).

| var_a | var_b | var_c | result |
| -| - | - | - |
| <code style="color:blue"><b>true</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> |
| <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:red"><b>false</b></code> | <code style="color:blue"><b>true</b></code> |

Then you can simply state that `result` is only true when either, (`var_a` is <code style="color:blue"><b>true</b></code> and `var_b` is <code style="color:red"><b>false</b></code> and `var_c` is <code style="color:red"><b>false</b></code>) or if (`var_a` is <code style="color:red"><b>false</b></code> and `var_b` is <code style="color:red"><b>false</b></code> and `var_c` is <code style="color:red"><b>false</b></code>). Otherwise `result` is <code style="color:red"><b>false</b></code>.

Thats almost a boolean expression in of itself! Lets just use the symbols we have and we'll be good to go.

```
result = (var_a && !var_b && !var_c) || (!var_a && !var_b && !var_c);
```

### Simplifying boolean expressions
This section is coming soon! If you see a problem requring this, please ask your mentor.
