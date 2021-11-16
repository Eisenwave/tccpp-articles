# Effective Variable Names
Good variable names:
- inform you of their purpose
- aren't too short or long
- aren't generic
- don't use confusing acronyms

Short variable names are fine as for loop counters.
## Bad Example
?inline
```c
int a;
int x = scanf("%d", &a);

if(x != 0)
    return -1;
    
printf("%d years old", x);
```
## Good Example
?inline
```c
int userAge;
int errorCode = scanf("%d", &userAge);

if(errorCode != 0)
    return -1;

printf("%d years old", userAge);
```

## Naming Conventions
Name your variables/functions in a consistent way. Here are some common naming conventions:
```c
int camelCase = ...;
int PascalCase = ...;
int snake_case = ...;
```
It doesn't matter which one you use, just make sure you keep your style consistent to keep your code clean.
## Also See
- [Short article on naming conventions](https://www.theserverside.com/feature/A-guide-to-common-variable-naming-conventions)

?creditFooter 614056212803092480
