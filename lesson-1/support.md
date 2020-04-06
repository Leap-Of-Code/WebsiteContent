## Key Takeways
* When you first create a variable you are `declaring` or `defining` it.
* Variable should be named in `lower_snake_case`.
* Some types are `int`, `float`, and `char`.
* `cin` is your code  prompting a user to give a reply. It will wait until a user indicates a response.

## Supplemental Information

### `string`
One type not discussed in the videos is a `string` type. The `string` type enables you to have variables of more than one character.

For example, you can't do
```cpp
char name = 'Joe';
```
Because a `char` type can only have one character. However you can do
```cpp
string name = "Joe";
```
Notice that you have to use `"` when creating a `string` vs `'` when creating a `char`.
#### `cin` for `string`
One slightly tricky thing for string is that you can't accept spaces in user input for a string. We'll cover how to do this in the future. While you can do:
```cpp
string name = "Abigale Night";
```
You won't **yet** be able to write code such as
```cpp
string name;
cin >> name;
```
where the user can input `Abigale Night`. However the user can input `Abigale` or `Night`, just not a `' '` in the middle.

#### "Math" with `string`
One cool thing about the `string` type is that you can "add" two of them.
```cpp
string first_name = "Abigale";
string last_name = "Night";
string full_name = first_name + " " + last_name;
```
What do you think `full_name` will be? It will be `Abigale Night`! This might also be a good solution to the `cin` issue we brought up earlier. Adding is the only "math" that will work with `string`.
