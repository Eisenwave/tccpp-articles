# Name Variables Effectively

Sometimes we don't really know how or what we should name a variable, and other times we are just lazy causing while naming a variable causing our code to be unmaintainable and unclear.

Good variable names:
- inform you of their purpose
- aren't too short or long
- aren't generic
- don't use confusing acronyms \
Short variable names are fine when part of short code blocks or as for loop counters.
## Example
```c
char* data = getData();
// bad; what kind of data is this?

for (int i; i < 10; ++i) ...
// fine, but could possibly be more informative...

int averageHairLengthRetrievedFromDatabase = 45;
// too long! Maybe put the retrieved data in a struct?

void* tca = grp;
// bad; what do these acronyms mean?

int studentGrades[5];
// perfect
```

## Naming Conventions

Try naming your variables/functions in a consistent way. Here are some common naming conventions:
```c
int camelCase = ...;
int PascalCase = ...;
int snake_case = ...;
```
It doesn't matter which one you use, just make sure you keep it consistent to keep your code clean.
