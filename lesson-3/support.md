## Key Takeaways
* Sizes are use the unit of "Bytes".
* Variable size correlates to the variable type. If you know the type of the variable, you know the size of the variable.
* `sizeof` command gives the size in bytes. You can enter any type.
```cpp
cout << "size: " << sizeof(int) << endl;
```


Type|Size (in bytes)|Min|Max
---|---|---|---
bool | 1 | 0 | 1
char | 1 | `TBD` | `TBD`
short | 2 | -2<sup>15</sup> | 2<sup>15</sup>-1
unsigned short | 2 | 0 | 2<sup>16</sup>-1
float | 4 | `TBD` | `TBD`
int<sup>+</sup> | 4 | -2<sup>31</sup> | 2<sup>31</sup>-1
unsigned int | 4 | 0 | 2<sup>32</sup>-1
long<sup>+</sup> | 4 | -2<sup>31</sup> | 2<sup>31</sup>-1
unsigned long | 4 | 0 | 2<sup>32</sup>-1
long long | 8 | -2<sup>63</sup> | 2<sup>63</sup>-1
unsigned long long | 8 | 0 | 2<sup>64</sup>-1
string | 8 | n/a | n/a

<sup>+</sup> `int` and `long` have the same values in the table, but they are different types. We'll come back to this in the future, but know this isn't a mistake!

## Supplemental Information
### const
Just like `unsigned` can be applied as a modifier to some numerical types, you can include the `const` modifier for any variable you wish to declare. The `const` modifier makes it so that the variable's value will not be able to be modified once you declare it - its constant. This can be applied to ALL types and should be used any time you know the variable shouldn't be changed.

```cpp
const int x = 10;
// This next line will cause this code to fail, as x is const and it's value can't be updated.
x = 10;
```

```cpp
const string example = "Test sentence.";
// This next line still works since we aren't changing the value of the variable example.
cout << example << endl;
```
