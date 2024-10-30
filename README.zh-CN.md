# 垃圾代码书写准则

[![State-of-the-art Shitcode](https://img.shields.io/static/v1?label=State-of-the-art&message=Shitcode&color=7B5804)](https://github.com/trekhleb/state-of-the-art-shitcode)

这是一个你的项目应该遵循的垃圾代码书写准则的列表，把称为适当的垃圾代码。

这是 C 语言的分支。

_Read this in other languages:_
[_English_](README.md),
[_한국어_](README.ko-KR.md)

## 获取你的徽章

如果你的代码库遵循最先进的 shitcode 原则，你可以使用以下“最先进的 shitcode”徽章：

[![最先进的 Shitcode](https://img.shields.io/static/v1?label=State-of-the-art&message=Shitcode&color=7B5804)](https://github.com/trekhleb/state-of-the-art-shitcode)

徽章的 Markdown 源代码：

```markdown
[![最先进的 Shitcode](https://img.shields.io/static/v1?label=State-of-the-art&message=Shitcode&color=7B5804)](https://github.com/trekhleb/state-of-the-art-shitcode)
```

## 原则

### 💩 命名变量时让代码看起来像已经被混淆过一样

少打字，省事儿。

_好的 👍🏻_

```c
int a = 42;
```

_坏的 👎🏻_

```c
int age = 42;
```

### 💩 混合变量与函数的命名风格

差异即美。。

_好的 👍🏻_

```c
int wWidth = 640;
int w_height = 480;
```

_坏的 👎🏻_

```c
int windowWidth = 640;
int windowHeight = 480;
```

### 💩 绝不要写注释

反正没有人会阅读你的代码。

_好的 👍🏻_

```c
const int cdr = 700;
```

_坏的 👎🏻_

```c
// 700ms 的数字是基于 UX A/B 测试结果经验性地计算出来的。
// @see: <链接到实验或相关 JIRA 任务或详细解释 700 的内容>
const int callbackDebounceRate = 700;
```

### 💩 始终用你的母语写注释

如果你违反了“没有注释”原则，那么至少试着用与代码语言不同的语言写注释。如果你的母语是英语，你可以违反这个原则。

_好的 👍🏻_

```c
// Закриваємо модальне віконечко при виникненні помилки.
toggleModal(false);
```

_坏的 👎🏻_

```c
// Hide modal window on error.
toggleModal(false);
```

### 💩 尽可能多地混合格式化风格

差异即美。

_好的 👍🏻_

```c
char ingredients[] = "tomato";
char* dressing = "mayonnaise";
```

_坏的 👎🏻_

```c
char* ingredients = "tomato";
char* dressing = "mayonnaise";
```

### 💩 尽可能多地将代码放在一行中

_好的 👍🏻_

```c
for(int i=0;i<10;i++){printf("%d",i);}
```

_坏的 👎🏻_

```c
for (int i = 0; i < 10; i++) {
    printf("%d", i);
}
```

### 💩 悄悄的发生错误

每当你捕捉到错误时，没必要让任何人知道。不要有日志，不要有错误提示，放轻松。

_好的 👍🏻_

```c
void doSomething() {
    // Something unpredictable.
}
```

_坏的 👎🏻_

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

### 💩 大量使用全局变量

Globalization原则。

_好的 👍🏻_

```c
int x = 5;

int square(int x) {
    return x * x;
}

int main() {
    x = square(x);
    // 现在 x 是 25。
}
```

_坏的 👎🏻_

```c
int square(int x) {
    return x * x;
}

int main() {
    int x = 5;
    x = square(x);
}
```

### 💩 创建你永远不会用的变量

以防万一。

_好的 👍🏻_

```c
int sum(int a, int b, int c) {
    int timeout = 1300;
    int result = a + b;
    return a + b;
}
```

_坏的 👎🏻_

```c
int sum(int a, int b) {
    return a + b;
}
```

### 💩 你需要有不会被执行的代码

这是你的“计划 B”。

_好的 👍🏻_

```c
int square(int num) {
    if (num == 0) {
        return 0;
    } else {
        return num * num;
    }
    return -1; // 这是我的“计划 B”。
}
```

_坏的 👎🏻_

```c
int square(int num) {
    if (num == 0) {
        return 0;
    }
    return num * num;
}
```

### 💩 三角原则

像鸟巢一样 - 嵌套，嵌套，无限嵌套。

_好的 👍🏻_

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

_坏的 👎🏻_

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

### 💩 混乱缩进

避免缩进，因为它们会使复杂的代码在编辑器中占用更多空间。如果你不想避免它们，那么就搞乱它们。

_好的 👍🏻_

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

_坏的 👎🏻_

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

### 💩 始终将布尔值命名为 `flag`

给你的同事留出思考布尔值含义的空间，这样可以锻炼他们的思维。

_好的 👍🏻_

```c
int flag = true;
```

_坏的 👎🏻_

```c
int isDone = false;
int isEmpty = false;
```

### 💩 长函数比短函数好

不要将程序逻辑划分为可读的部分。如果你的 IDE 的搜索崩溃了，你将无法找到必要的文件或函数。

- 一个 .c 文件中 10000 行代码是可以的。
- 一个函数体中 1000 行代码是可以的。
- 在一个 service.c 中处理多个库（标准和自定义，还有一些宏、手动内存管理和自定义字符串操作）？可以。

### 💩 避免为你的代码编写测试

这是一种重复和不必要的工作。

### 💩 尽可能避免代码 linter

按照自己的想法写代码，尤其是当团队中有不止一个开发人员时。这是“自由”原则。

### 💩 开始项目时没有 README 文件

并且暂时保持这种状态。

### 💩 你需要有不必要的代码

不要删除你的应用程序不使用的代码。最多只需注释掉它。