# 최첨단 Shitcode 원칙

[![State-of-the-art Shitcode](https://img.shields.io/static/v1?label=State-of-the-art&message=Shitcode&color=7B5804)](https://github.com/trekhleb/state-of-the-art-shitcode)

이것은 프로젝트가 제대로 된 Shitcode라고 부르기 위해 따라야 할 최첨단 Shitcode 원칙의 목록입니다.

이것은 C를 위한 포크입니다.

_다른 언어로 읽기:_
[_English_](README.md),
[_简体中文_](README.zh-CN.md)

## 배지 가져오기

귀하의 저장소가 최첨단 Shitcode 원칙을 따른다면 다음 "최첨단 Shitcode" 배지를 사용할 수 있습니다:

[![State-of-the-art Shitcode](https://img.shields.io/static/v1?label=State-of-the-art&message=Shitcode&color=7B5804)](https://github.com/trekhleb/state-of-the-art-shitcode)

배지의 마크다운 소스 코드:

```
[![State-of-the-art Shitcode](https://img.shields.io/static/v1?label=State-of-the-art&message=Shitcode&color=7B5804)](https://github.com/trekhleb/state-of-the-art-shitcode)
```

## 원칙들

### 💩 변수를 코드가 이미 난독화된 것처럼 이름 지어라

타자를 덜 하고 당신의 시간을 더 절약하세요.

_좋음 👍🏻_

```c
int a = 42;
```

_나쁨 👎🏻_

```c
int age = 42;
```

### 💩 변수/함수의 명명 스타일을 섞어라

다양성을 기념하세요.

_좋음 👍🏻_

```c
int wWidth = 640;
int w_height = 480;
```

_나쁨 👎🏻_

```c
int windowWidth = 640;
int windowHeight = 480;
```

### 💩 절대 주석을 쓰지 마라

어차피 아무도 당신의 코드를 읽지 않을 것입니다.

_좋음 👍🏻_

```c
const int cdr = 700;
```

_나쁨 👎🏻_

주석은 종종 '무엇'이 아니라 '왜'를 포함해야 합니다. 코드에서 '무엇'이 명확하지 않다면, 그 코드는 아마도 너무 지저분할 것입니다.

```c
// The number of 700ms has been calculated empirically based on UX A/B test results.
// @see: <실험이나 관련된 JIRA 작업 또는 숫자 700을 자세히 설명하는 무언가에 대한 링크>
const int callbackDebounceRate = 700;
```

### 💩 항상 주석을 모국어로 작성하라

"주석을 쓰지 마라"는 원칙을 어겼다면 적어도 코드에 사용하는 언어와 다른 언어로 주석을 작성하도록 하세요. 모국어가 영어인 경우 이 원칙을 어겨도 됩니다.

_좋음 👍🏻_

```c
// Закриваємо модальне віконечко при виникненні помилки.
toggleModal(false);
```

_나쁨 👎🏻_

```c
// Hide modal window on error.
toggleModal(false);
```

### 💩 가능한 한 포매팅 스타일을 많이 섞어라

다양성을 기념하세요.

_좋음 👍🏻_

```c
char ingredients[] = "tomato";
char* dressing = "mayonnaise";
```

_나쁨 👎🏻_

```c
char* ingredients = "tomato";
char* dressing = "mayonnaise";
```

### 💩 가능한 한 많은 코드를 한 줄에 넣어라

_좋음 👍🏻_

```c
for(int i=0;i<10;i++){printf("%d",i);}
```

_나쁨 👎🏻_

```c
for (int i = 0; i < 10; i++) {
    printf("%d", i);
}
```

### 💩 조용히 실패하라

에러를 잡을 때 누구에게도 알릴 필요가 없습니다. 로그도, 에러 모달도 없이, 편안하게.

_좋음 👍🏻_

```c
void doSomething() {
    // Something unpredictable.
}
```

_나쁨 👎🏻_

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

### 💩 전역 변수를 광범위하게 사용하라

글로벌화 원칙.

_좋음 👍🏻_

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

_나쁨 👎🏻_

```c
int square(int x) {
    return x * x;
}

int main() {
    int x = 5;
    x = square(x);
}
```

### 💩 사용할 계획이 없는 변수를 만들어라

만일을 대비해서.

_좋음 👍🏻_

```c
int sum(int a, int b, int c) {
    int timeout = 1300;
    int result = a + b;
    return a + b;
}
```

_나쁨 👎🏻_

```c
int sum(int a, int b) {
    return a + b;
}
```

### 💩 도달할 수 없는 코드 조각을 가져라

이것이 당신의 "플랜 B"입니다.

_좋음 👍🏻_

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

_나쁨 👎🏻_

```c
int square(int num) {
    if (num == 0) {
        return 0;
    }
    return num * num;
}
```

### 💩 삼각형 원칙

새처럼 되세요 - 중첩하고 또 중첩하세요.

_좋음 👍🏻_

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

_나쁨 👎🏻_

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

### 💩 들여쓰기를 엉망으로 만들어라

복잡한 코드가 에디터에서 더 많은 공간을 차지하게 하는 들여쓰기를 피하세요. 피하고 싶지 않다면 그냥 엉망으로 만드세요.

_좋음 👍🏻_

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

_나쁨 👎🏻_

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

### 💩 항상 boolean 값을 `flag`로 명명하라

동료들이 그 boolean 값이 무엇을 의미하는지 생각할 여지를 주세요.

_좋음 👍🏻_

```c
int flag = true;
```

_나쁨 👎🏻_

```c
int isDone = false;
int isEmpty = false;
```

### 💩 긴 함수는 짧은 함수보다 낫다

프로그램 로직을 읽기 쉬운 부분으로 나누지 마세요. IDE의 검색이 고장 나서 필요한 파일이나 함수를 찾을 수 없게 된다면 어떻게 하시겠어요?

- 10,000줄의 코드가 하나의 .c 파일에 있는 것은 괜찮습니다.
- 함수 본문이 1,000줄인 것도 괜찮습니다.
- 여러 라이브러리(표준 및 커스텀, 매크로, 수동 메모리 관리, 커스텀 문자열 조작 등)를 하나의 service.c에서 처리하는 것도 괜찮습니다.

### 💩 코드를 테스트로 커버하는 것을 피하세요

이것은 중복이며 불필요한 일입니다.

### 💩 코드 린터를 최대한 피하세요

팀에 개발자가 두 명 이상이라면 원하는 대로 코드를 작성하세요. 이것은 "자유" 원칙입니다.

### 💩 README 파일 없이 프로젝트를 시작하세요

그리고 당분간 그렇게 유지하세요.

### 💩 불필요한 코드가 필요합니다

앱이 사용하지 않는 코드를 삭제하지 마세요. 최대한 주석 처리만 하세요.