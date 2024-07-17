# Rust Studying

This is my first repo for trying out rust.
- So this repository includes modifications made by me base on [rust-python-book](https://github.com/Indosaram/rust-python-book?tab=readme-ov-file).

## 러스트 시작
1. 러스트 툴체인 설치
    ``` shell
    $ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
    ```
2. rust analyzer 설치(vsc extention)

## Make Project
```shell
cargo new {project_name}
```

- 구조 예시
```
rust_part
├── Cargo.lock
├── Cargo.toml * 
├── src * 
│   ├── main.rs * 
│   ├── lib.rs
│   ├── bin
│   │   └── another_binary.rs
│   └── modules
│       └── mod1.rs
└── tests
    └── integration_test.rs
```
별표 친 부분은 처음부터 만들어진 파일을 의미합니다. 
- Cargo.toml
    - 설명: 프로젝트의 메타데이터와 의존성을 관리하는 파일
- src/main.rs
    - Rust 프로그램의 진입점(Entry point) 파일

그외 생성될 수 있는 파일은 아래와 같다.
- Cargo.lock
    - 프로젝트의 모든 의존성의 정확한 버전을 기록하는 파일입니다. Cargo.toml의 변경 없이 의존성을 재현할 수 있도록 합니다.
- src/lib.rs
    - 라이브러리 모드로 작성된 코드를 포함하는 파일입니다. lib.rs는 주로 여러 모듈을 포함하고 내보내는 역할을 합니다.
- src/bin/
    - 추가적인 바이너리 파일을 포함하는 디렉토리입니다. 여기에는 main.rs와 별도로 실행될 수 있는 다른 바이너리 파일이 들어갑니다.
- src/modules/
    - 프로젝트 내의 모듈을 포함하는 디렉토리입니다. 예를 들어, mod1.rs는 mod1이라는 모듈을 정의합니다.
- tests/
    - 통합 테스트를 포함하는 디렉토리입니다. integration_test.rs 파일은 통합 테스트 코드를 포함합니다.

## Run Rust Code
``` shell
rust_first git:(master) ✗ cargo run
   Compiling rust_first v0.1.0 (/home/skyriver/Documents/rust_tut/rust_first)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 4.85s
     Running `target/debug/rust_first`
Hello, world!
```
- 볼 수 있듯이 `cargo build`를 통해 만들어진 컴파일 결과, 즉 `target/debug/{project_name}`에 바이너리 파일이 만들어지게 됩니다.
- 이를 실행할 수 있으며, debug 모드이기 때문에, release 세팅을 위해서는 아래와 같이 처리해야 합니다.
```shell
$ cargo build --release

Compiling notebook v0.1.0 (/Users/code/temp)
 Finished release [optimized] target(s) in 1.34s
```

- 포매팅 기능 `alt(opt) + shift + F`도 가능하다고 한다. 
```shell
cargo fmt
```