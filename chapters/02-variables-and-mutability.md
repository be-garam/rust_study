
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