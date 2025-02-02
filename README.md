# tree-sitter

## tree-sitter 0.20.8 버전 기반

[![CICD badge]][CICD]
[![DOI](https://zenodo.org/badge/14164618.svg)](https://zenodo.org/badge/latestdoi/14164618)

[CICD badge]: https://github.com/tree-sitter/tree-sitter/actions/workflows/CICD.yml/badge.svg
[CICD]: https://github.com/tree-sitter/tree-sitter/actions/workflows/CICD.yml

Tree-sitter is a parser generator tool and an incremental parsing library. It can build a concrete syntax tree for a source file and efficiently update the syntax tree as the source file is edited. Tree-sitter aims to be:

- **General** enough to parse any programming language
- **Fast** enough to parse on every keystroke in a text editor
- **Robust** enough to provide useful results even in the presence of syntax errors
- **Dependency-free** so that the runtime library (which is written in pure C) can be embedded in any application

## Links

- [Documentation](https://tree-sitter.github.io)
- [Rust binding](lib/binding_rust/README.md)
- [WASM binding](lib/binding_web/README.md)
- [Command-line interface](cli/README.md)

## 변경점
- 일부 소스 코드 수정(start line과 end line이 달라도 텍스트가 출력되도록)
- 변경 부분 [[link]](https://github.com/tree-sitter/tree-sitter/compare/master...leebs0521:tree-sitter:master#diff-518c48ee9177a60a58a06a7e24beeffad37f9a1c109c85fac295e63754ff6e86)
## 빌드 방법

0. 사전 준비(Rust 설치)
<pre>
<code>
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
cargo --version
</code>
</pre>

1. git clone
<pre>
<code>
git clone https://github.com/leebs0521/tree-sitter.git
cd tree-sitter
</code>
</pre>

2. Build the Rust libraies and CLI:
<pre>
<code>
cargo build --release
</code>
</pre>

3. Tree-sitter 위치
<pre>
<code>
tree-sitter/target/release/tree-sitter
</code>
</pre>

4. Tree-sitter 초기 설정
<pre>
<code>
cd tree-sitter/target/release
./tree-sitter init-config
head -n 6 ~/.config/tree-sitter/config.json
</code>
</pre>

아래 디렉토리에 생성 후 아래의 언어별 tree-sitter parser 레포지토리 클론
c, cpp, go, objective-c, swift
<pre>
<code>
{
  "parser-directories": [
    "/your_home_directory/github",
    "/your_home_directory/src",
    "/your_home_directory/source"
  ],
  ...
}
</code>
</pre>

## tree-sitter 언어 별 parser
```shell
  mkdir /your_home_directory/source
  cd /your_home_directory/source
  git clone {언어별(c, cpp, go, objective-c, swift) 파서 레포지토리}
```
1. [c parser](https://github.com/tree-sitter/tree-sitter-c)
2. [cpp parser](https://github.com/tree-sitter/tree-sitter-cpp)
3. [go parser](https://github.com/tree-sitter/tree-sitter-go)
4. [objective-c parser](https://github.com/amaanq/tree-sitter-objc)
5. [swift parser](https://github.com/syrose01/tree-sitter-swift)