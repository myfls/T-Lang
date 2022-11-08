# T-Lang

A Tensor based Programing Language.

## Usage

### How to build

```bash
git clone git@github.com:WLFJ/T-Lang.git
git submodule update --init --depth 1
mkdir 3rdparty/llvm-project/build && cd 3rdparty/llvm-project/build
# LLVM_ENABLE_RTTI=true is needed.
cmake -G Ninja ../llvm \
   -DLLVM_ENABLE_PROJECTS=mlir \
   -DLLVM_BUILD_EXAMPLES=ON \
   -DLLVM_TARGETS_TO_BUILD="X86;NVPTX;AMDGPU" \
   -DCMAKE_BUILD_TYPE=Release \
   -DLLVM_ENABLE_ASSERTIONS=ON
cd -
mkdir build && cd build
cmake ..
cmake --build .
```

## How to extend the compiler

1. Edit `parser.yy` to set what grammer you want.
2. According to `parser`, you may want to add token support in `scanner.ll`
3. The same thing in `AST.hpp` and `AST.cpp`.

## How to write test cases

Coming Soon ...

## TO-DO

- [x] A simple (hello-world example) bison example.
- [x] A flex.
- [x] A AST dumper.
- [x] CMake
- [x] Migrate build system from `GNU make` to `CMake`.
- [x] ~~Mem safer (avoid useing `new` directly, instead of `unique_ptr`?).~~ No, we'll use AST from ToyLang.
- [x] ~~Simplify `yy` and `ll` file.~~ Seems it's already clean yet.
- [x] Freeze MLIR into `3rdparty`, and include it into CMakeLists. (Should we build it automatically ?).
- [x] Add backend support.
- [x] Support `print` in grammar.
- [x] Add `TIR`, make them all runnable.
- [x] Add variable dec like `var a = 1;`. (partial, id bind in grammar is needed.)
- [ ] Add math calc. (for `+` `-` `*` `.`)
- [ ] Add function fully support. (arbitary argument, return value, caller, callee).
- [ ] Add remain supported expr.
- [ ] ~~Dump `llvm::Module` into file.~~ using JIT instead.
- [ ] Add RTTI support cmd.
- [ ] FileCheck (LLVM is needed).
- [ ] Automatic Test.(Maybe `cmake test`).
