
## Navigating the Website

### Assignments

#### Types of questions
There are 3 different types of questions. Each question will provide a different form of practice. If you get stuck on one, feel free to take a break from it and try a different question.

##### Review Questions
These exist as a review, there progress is not saved or shared, and will provide you reference for some concepts the videos touched on. They can be used for examples of both good and bad code depending on the question. Be sure to them prior to actually starting on the assignment.

##### Fix Code Question
These questions have a suite of hand picked errors to help you practice. Often they don't involve lots of coding, but do involve lots of detail orientation. Some problems may have multiple issues!

##### Invent Code Question
These questions are most likely going to be the most challenging. Then often start with a clean slate and rely on your ability to craft code from scratch. Thats why they should be left until the end.

### Code Reviews
Once you've marked all your questions as complete, you'll get the opportunity to submit your assignment. This will create a code review for it and additionally open you up for code reviews for other's assignments for that topic as well. As you get comments, but sure to return and update your assignment with comments fixed!

## Key Takeways
* Errors are the way the computer communicates with you regarding your code.
* You're never going to stop making errors, its a normal part of programming.
* To solve the errors, just scroll to the top, and try fixing __only__ the first one.
  * Just hit the run button to check if you have fixed it!

## Supplemental Information

### `\n` vs `endl`
You may have noticed that there was a `\n` at the end of the example on [Repl](https://repl.it/repls).
That is how you add a new line (enter key in MS Word). Try adding and removing `\n` and seeing you notice a difference. `endl` can also be used to print out a new line. In general, we prefer using:
```cpp
cout << "Hello world";
cout << endl;
```
over using
```cpp
cout << "Hello world\n";
```

### Interpreting C++ Errors
When getting errors you may be a bit overwhelmed initially. But it just takes some practing to get used to reading them. Lets take the following as an example:
```
% run
Building...
main.cpp:6:11: error: use of undeclared identifier 'Hello'; did you mean 'ftello'?
  cout << Hello;
          ^~~~~
          ftello
/usr/include/stdio.h:142:7: note: 'ftello' declared here
off_t ftello(FILE *);
      ^
main.cpp:6:11: error: address of function 'ftello' will always evaluate to 'true' [-Werror,-Wpointer-bool-conversion]
  cout << Hello;
       ~~ ^~~~~
main.cpp:6:11: note: prefix with the address-of operator to silence this warning
  cout << Hello;
          ^
          &
2 errors generated.
Build failed.
```

When you read this, reading the last two lines
```
2 errors generated.
Build failed.
```
indicates that your program wasn't able to build correctly, and there are currently two errors you need to fix.

Then we jump back to the top and notice that the first error is:
```
main.cpp:6:11: error: use of undeclared identifier 'Hello'; did you mean 'ftello'?
  cout << Hello;
          ^~~~~
          ftello
/usr/include/stdio.h:142:7: note: 'ftello' declared here
off_t ftello(FILE *);
      ^
```
We know the error begins there because the line starts with:
```
main.cpp:[first_number]:[second_number] error:
```
where `first_number = 6`, `second_number = 11`. Notice that the error ends **ONLY** once you get to the next line that begins with the same pattern. Otherwise all lines underneath are related to the same error. `first_number` represents the line where the error happend, so in this case `Line 6`, and `second_number` represents the character where the error happened `Character 11`. I often find it sufficient to use just `first_number`.

The second error in this log is:
```
main.cpp:6:11: error: address of function 'ftello' will always evaluate to 'true' [-Werror,-Wpointer-bool-conversion]
  cout << Hello;
       ~~ ^~~~~
main.cpp:6:11: note: prefix with the address-of operator to silence this warning
  cout << Hello;
          ^
          &
```

Its ok if you look at this error log and are confused. I mean, what is a `ftello`? Sometimes the computer can't really know what you are trying to do, so when it gives you hints about the errors, it may throw something meaningless at you. If the words in the error don't make sense, try asking others a question about it. You both may learn something new.

Now I'm not going to spoil this question, as this is an assignment, but hopefully by seeing the code, and the error log, you'll be able to make some progress.
