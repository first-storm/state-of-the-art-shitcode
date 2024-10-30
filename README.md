# State-of-the-Art Shitcode Principles

[![State-of-the-art Shitcode](https://img.shields.io/static/v1?label=State-of-the-art&message=Shitcode&color=7B5804)](https://github.com/trekhleb/state-of-the-art-shitcode)

This a list of state-of-the-art shitcode principles your project should follow to call it a proper shitcode.

This is the fork for C.

_Read this in other languages:_
[_简体中文_](README.zh-CN.md),
[_한국어_](README.ko-KR.md)

## Get Your Badge

If your repository follows the state-of-the-art shitcode principles you may use the following "state-of-the-art shitcode" badge:

[![State-of-the-art Shitcode](https://img.shields.io/static/v1?label=State-of-the-art&message=Shitcode&color=7B5804)](https://github.com/trekhleb/state-of-the-art-shitcode)

Markdown source-code for the badge:

```
[![State-of-the-art Shitcode](https://img.shields.io/static/v1?label=State-of-the-art&message=Shitcode&color=7B5804)](https://github.com/trekhleb/state-of-the-art-shitcode)
```

## The Principles

### 💩 Name variables in a way as if your code was already obfuscated

Fewer keystrokes, more time for you.

_Good 👍🏻_

```c
int a = 42;
```

_Bad 👎🏻_

```c
int age = 42;
```

### 💩 Mix variable/functions naming style

Celebrate the difference.

_Good 👍🏻_

```c
int wWidth = 640;
int w_height = 480;
```

_Bad 👎🏻_

```c
int windowWidth = 640;
int windowHeight = 480;
```

### 💩 Never write comments

No one is going to read your code anyway.

_Good 👍🏻_

```c
const int cdr = 700;
```

_Bad 👎🏻_

More often comments should contain some 'why' and not some 'what'. If the 'what' is not clear in the code, the code is probably too messy.

```c
// The number of 700ms has been calculated empirically based on UX A/B test results.
// @see: <link to experiment or to related JIRA task or to something that explains number 700 in details>
const int callbackDebounceRate = 700;
```

### 💩 Always write comments in your native language

If you violated the "No comments" principle then at least try to write comments in a language that is different from the language you use to write the code. If your native language is English you may violate this principle.

_Good 👍🏻_

```c
// Закриваємо модальне віконечко при виникненні помилки.
toggleModal(false);
```

_Bad 👎🏻_

```c
// Hide modal window on error.
toggleModal(false);
```

### 💩 Try to mix formatting style as much as possible

Celebrate the difference.

_Good 👍🏻_

```c
char ingredients[] = "tomato";
char* dressing = "mayonnaise";
```

_Bad 👎🏻_

```c
char* ingredients = "tomato";
char* dressing = "mayonnaise";
```

### 💩 Put as much code as possible into one line

_Good 👍🏻_

```c
for(int i=0;i<10;i++){printf("%d",i);}
```

_Bad 👎🏻_

```c
for (int i = 0; i < 10; i++) {
    printf("%d", i);
}
```

### 💩 Fail silently

Whenever you catch an error it is not necessary for anyone to know about it. No logs, no error modals, chill.

_Good 👍🏻_

```c
void doSomething() {
    // Something unpredictable.
}
```

_Bad 👎🏻_

```c
void doSomething() {
    // Something unpredictable.
    if (error_occurred) {
        logError();
        // And/Or
        showErrorMessage();
    }
}
```

### 💩 Use global variables extensively

Globalization principle.

_Good 👍🏻_

```c
int x = 5;

int square(int x) {
    return x * x;
}

int main() {
    x = square(x);
    // Now x is 25.
}
```

_Bad 👎🏻_

```c
int square(int x) {
    return x * x;
}

int main() {
    int x = 5;
    x = square(x);
}
```

### 💩 Create variables that you're not going to use.

Just in case.

_Good 👍🏻_

```c
int sum(int a, int b, int c) {
    int timeout = 1300;
    int result = a + b;
    return a + b;
}
```

_Bad 👎🏻_

```c
int sum(int a, int b) {
    return a + b;
}
```

### 💩 You need to have an unreachable piece of code

This is your "Plan B".

_Good 👍🏻_

```c
int square(int num) {
    if (num == 0) {
        return 0;
    } else {
        return num * num;
    }
    return -1; // This is my "Plan B".
}
```

_Bad 👎🏻_

```c
int square(int num) {
    if (num == 0) {
        return 0;
    }
    return num * num;
}
```

### 💩 Triangle principle

Be like a bird - nest, nest, nest.

_Good 👍🏻_

```c
void someFunction() {
    if (condition1) {
        if (condition2) {
            if (condition3) {
                for (;;) {
                    if (condition4) {
                        // Do something.
                    }
                }
            }
        }
    }
}
```

_Bad 👎🏻_

```c
void someFunction() {
    if (!condition1 || !condition2 || !condition3) {
        return;
    }
    for (;;) {
        if (condition4) {
            // Do something.
        }
    }
}
```

### 💩 Mess with indentations

Avoid indentations since they make complex code take up more space in the editor. If you're not feeling like avoiding them then just mess with them.

_Good 👍🏻_

```c
#include<stdio.h>

int main() {
    char *fruits[] = {
    "apple", "orange",
        "grape", "pineapple"
};
        char *toppings[] = {
            "syrup","cream", "jam", "chocolate"
};char desserts[16][50];
int count = 0;
        int i = 0,
                j = 0;
for (i = 0; i < 4; i++) {
        for (j = 0; j < 4; j++) {
sprintf(desserts[count],
"%s with %s", fruits[i], toppings[j]);
printf("%s\n", desserts[count]);
count++;}}
    return 0;
    }
```

_Bad 👎🏻_

```c
#include <stdio.h>

int main() {
    char *fruits[] = {"apple", "orange", "grape", "pineapple"};
    char *toppings[] = {"syrup", "cream", "jam", "chocolate"};
    char desserts[16][50];
    int count = 0;
    int i = 0, j = 0;
    
    for (i = 0; i < 4; i++) {
        for (j = 0; j < 4; j++) {
            sprintf(desserts[count], "%s with %s", fruits[i], toppings[j]);
            printf("%s\n", desserts[count]);
            count++;
        }
    }
    
    return 0;
}
```

### 💩 Always name your boolean value a `flag`

Leave the space for your colleagues to think what the boolean value means.

_Good 👍🏻_

```c
int flag = true;
```

_Bad 👎🏻_

```c
int isDone = false;
int isEmpty = false;
```

### 💩 Long-read functions are better than short ones.

Don't divide a program logic into readable pieces. What if your IDE's search breaks and you will not be able to find the necessary file or function?

- 10000 lines of code in one .c file is OK.
- 1000 lines of a function body is OK.
- Handling multiple libraries (standard and custom, also, there are some macros, manual memory management, and custom string manipulation) in one service.c? It's OK.

### 💩 Avoid covering your code with tests

This is a duplicate and unnecessary amount of work.

### 💩 As hard as you can try to avoid code linters

Write code as you want, especially if there is more than one developer in a team. This is a "freedom" principle.

### 💩 Start your project without a README file.

And keep it that way for the time being.

### 💩 You need to have unnecessary code

Don't delete the code your app doesn't use. At most, comment it.
