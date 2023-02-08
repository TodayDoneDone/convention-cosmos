# 리소스

### strings.xml

- 주제_설명

> notification_access_permission
> storage_permission_granted

### drawable

- 용도_타입_설명_사이즈

> bg_baseline_gradient_500

### colors.xml

- 색이름_강도(optional)

> red
> blue_200
> blue_400
> blue_600

### View ID

- 타입_설명

> tv_header
> tv_title
> btn_register

# 파일

### 기본 원칙

- top-level 함수 100% 파일과 클래스 100% 파일 별도 분리
   - top-level 함수와 클래스가 섞여있는 파일 ❌

### top-level 함수 100% 파일 네이밍

- `합성어`는 `파스칼 케이스`로, `한 단어`는 `소문자`로 처리

### top-level 확장 함수 100% 파일일 경우 네이밍

- extension의 receiver 대상으로 네이밍

> TextView.kt
> Int.kt
> String.kt

# Code

### 상수 표기법

- 모두 대문자 + 스네이크

### 함수 반환 표현

- 한 줄 수식어로 완성되는 함수를 제외하면 모두 명시적 `return`  사용
- `when`이 사용되는 경우 `when`의 모든 블록이 한 줄 수식어로 완성되는 경우에만 `return` 생략 허용

```kotlin
fun `이렇게 하면 안 됨`() = a.b.c.d.e.f.g
fun `이렇게 해도 됨`(number: Int) = number * 2

fun `이렇게 하면 안 됨 - 2`(isTrue: Boolean) = when(isTrue) {
    true -> a.b.c.d.e.f.g
    false -> isTrue.asInt() * 2
}
fun `이렇게 해도 됨 - 2()`(isTrue: Boolean) = when(isTrue) {
    true -> isTrue.asInt() * 1
    false -> isTrue.asInt() * 2
}
```

### When 블록 괄호

- 한 줄 표현 가능할 때는 괄호 생략
- 두 줄 표현 이상은 괄호 필수 사용

```kotlin
fun `when convention`(isTrue: Boolean) {
    when(isTrue) {
        true -> you_are_awesome()
        false -> {
            `Do you think you're awesome?`()
            `yes`()
        }
    }
}
```

### if 문

- 괄호 필수 사용
- 조건이 2개 이상 들어가는 경우 각각 개행

```kotlin
// BAD
if (true) { `Do you think you're awesome?`() }
    
// GOOD
if (true) {
    you_are_awesome()
}

// BAD
if(`am i awesome?`() && true) {
    awesome_magic()
}

// GOOD
if (
    `am i awesome?`() &&
    true
) {
    awesome_magic()
}
```
