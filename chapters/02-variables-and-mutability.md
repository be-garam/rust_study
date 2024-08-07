
## 값 출력
```rust
fn main() {
    let x = 5;
    println!("The value of x is: {}", x);
}
```
```python
def main():
    x = 5
    print(f"The value of x is: {x}")
```
- `python` print: 미리 정의된 함수로 간단하게 출력
- `rust` macro: 컴파일 시간에 코드를 생성하는 메타 프로그래밍 기능을 사용하여 출력
    - 이름 뒤에 `!`를 붙여서 일반 함수와 구분
    - 다양한 인자 수와 타입을 받을 수 있음

## 변수 선언
```rust
fn main() {
    let x: f64 = 3.0;
    let y = 10;

    pringln!("x: {}, y: {}", x, y);
}
```
```python
def main():
    x = 3.0
    y = 10

    print(f"x: {x}, y: {y}")
```

- `rust` 변수 선언: `let` 키워드로 시작
    - 변수명 뒤에 `:`을 붙여 타입을 명시
    - 타입 생략 시 컴파일러가 추론
        - 몇몇 경우에는 타입을 명시해야 함

## naming rule
<table><thead><tr><th></th><th>파이썬</th><th>러스트</th></tr></thead><tbody>
<tr><td>변수</td><td><code class="hljs">snake_case = 3</code></td><td><code class="hljs">let snake_case = 3;</code></td></tr>
<tr><td>함수</td><td><code class="hljs">def my_function</code></td><td><code class="hljs">fn my_function</code></td></tr>
<tr><td>클래스/구조체</td><td><code class="hljs">class MyClass</code></td><td><code class="hljs">struct MyStruct</code></td></tr>
<tr><td>상수</td><td><code class="hljs">SCREAMING_SNAKE_CASE = 1</code></td><td><code class="hljs">const SCREAMING_SNAKE_CASE: i32 = 1;</code></td></tr>
</tbody></table>

- 변수, 함수: `snake_case`
- 클래스, 구조체: `PascalCase`
    - 대문자로 시작하는 단어가 연결된 형태: camelCase에서 첫 단어도 대문자로 시작
- 상수: `SCREAMING_SNAKE_CASE`

## 불변성
```rust
fn main() {
    let x = 5;
    x = 6; // error
    println!("The value of x is: {}", x);
}
```
- run `cargo build --release`

**error message**
``` shell
error[E0384]: cannot assign twice to immutable variable `x`
 --> src/main.rs:3:5
  |
2 |     let x = 5;
  |         -
  |         |
  |         first assignment to `x`
  |         help: consider making this binding mutable: `mut x`
3 |     x = 6; // error
  |     ^^^^^ cannot assign twice to immutable variable
```
- 변수가 불변(immutable)하기 때문에 값을 두 번 할당할 수 없다고 이야기
- "help" 메시지에 따라 `mut` 키워드를 사용하여 변수를 가변(mutable)로 만들 수 있음

```rust
fn main() {
    let mut x = 5;
    x = 6; // error
    println!("The value of x is: {}", x);
}
```
## shadowing
```rust
fn main() {
    let x = "hello";
    let x = 3; // x is now of type i32
    println!("The value  of x is: {}",x);
}
```
- 변수명을 재사용하여 새로운 변수를 만드는 것을 shadowing이라고 함
- `let` 키워드를 사용하여 변수를 다시 선언하면 이전 변수를 가려버림
    - 새로운 변수이기 때문에 타입이 달라도 상관 없음
- 즉, let 키워드를 사용하여 변수를 재사용할 수 있음

## 데이터 타입
<table><thead><tr><th>이름</th><th>타입</th></tr></thead><tbody>
<tr><td>8비트 정수</td><td><code class="hljs">i8</code></td></tr>
<tr><td>16비트 정수</td><td><code class="hljs">i16</code></td></tr>
<tr><td>32비트 정수</td><td><code class="hljs">i32</code></td></tr>
<tr><td>64비트 정수</td><td><code class="hljs">i64</code></td></tr>
<tr><td>128비트 정수</td><td><code class="hljs">i128</code></td></tr>
<tr><td>아키텍처</td><td><code class="hljs">isize</code></td></tr>
<tr><td>부호 없는 8비트 정수</td><td><code class="hljs">u8</code></td></tr>
<tr><td>부호 없는 16비트 정수</td><td><code class="hljs">u16</code></td></tr>
<tr><td>부호 없는 32비트 정수</td><td><code class="hljs">u32</code></td></tr>
<tr><td>부호 없는 64비트 정수</td><td><code class="hljs">u64</code></td></tr>
<tr><td>부호 없는 128비트 정수</td><td><code class="hljs">u128</code></td></tr>
<tr><td>부호 없는 아키텍처</td><td><code class="hljs">usize</code></td></tr>
<tr><td>불리언</td><td><code class="hljs">bool</code></td></tr>
<tr><td>문자열</td><td><code class="hljs">String</code></td></tr>
<tr><td>문자열 슬라이스</td><td><code class="hljs">str</code></td></tr>
<tr><td>32비트 부동소수점 실수</td><td><code class="hljs">f32</code></td></tr>
<tr><td>64비트 부동소수점 실수</td><td><code class="hljs">f64</code></td></tr>
</tbody></table>

| isize 와 usize 는 컴퓨터 아키텍처가 32비트인지 64비트인지에 따라서 값이 달라지는 기본 포인터 크기

**타입 추론**
- 변수를 선언할 때 타입을 명시하지 않아도 rust-analyzer가 타입을 추론해서 화면에 보여주는 것처럼 컴파일러도 타입을 추론해서 변술르 선언
    - 기본값은 정수는 i32, 부동소수점(실수)은 f64

**Casting**
```rust
fn main() {
    let x: f64 = 1.2;
    let y = x as i32;
    println!("{} -> {}", x, y);
}
```
- `f64` 타입의 `x`를 `i32` 타입의 `y`로 변환
``` shell
1.2 -> 1
```
- Python에서는 타입 이름을 바로 사용하여 변환하지만, Rust에서는 `as` 키워드를 사용하여 변환

## CONSTANTS
```rust
const THRESHOLD: i32 = 10;

fn is_big(n: i32) -> bool {
    n > THRESHOLD
}

fn main() {
    println!("{}", THRESHOLD);
    println!("{}", is_big(5));

    THRESHOLD = 5;
}
intln!("{}", is_big(5));
}
```
- 상수는 `const` 키워드를 사용하여 일반적으로 모듈의 최상위에 선언
    - 모든 범위에서 상수에 접근하는 것이 가능
- Python에서 immutable 변수를 대문자로 선언하여 상수처럼 사용하는 것과 비슷하지만
    - Rust에서는 `const` 키워드를 사용하여 상수를 명시적으로 선언
    - Python에서는 상수를 변경될 수 있다는 점이 차이가 있다.

**error message**
``` shell
error[E0070]: invalid left-hand side of assignment
  --> src/main.rs:11:15
   |
11 |     THRESHOLD = 5;
   |     --------- ^
   |     |
   |     cannot assign to this expression
```
