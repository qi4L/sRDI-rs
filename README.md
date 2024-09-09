# sRDI-rs

Rust 实现的反射式 DLL 注入的 Shellcode 实现。将 DLL 转换为位置无关的 shellcode。

## Features

- 基于 [KCon2024高级恶意软件开发之RDI的进化](https://github.com/knownsec/KCon/blob/master/2024/%E9%AB%98%E7%BA%A7%E6%81%B6%E6%84%8F%E8%BD%AF%E4%BB%B6%E5%BC%80%E5%8F%91%E4%B9%8BRDI%E7%9A%84%E8%BF%9B%E5%8C%96.pdf)

## Usage

[Install Rust](https://www.rust-lang.org/tools/install)

构建项目
```
cargo build --release
```

- sRDI

```
Shellcode Reflective DLL Injection (sRDI)

Usage: srdi.exe [OPTIONS] --loader <LOADER> --payload <PAYLOAD> --function <FUNCTION> --parameter <PARAMETER> --output <OUTPUT>

Options:
      --loader <LOADER>        The reflective loader DLL path (loader.dll)
      --payload <PAYLOAD>      The payload DLL path (payload.dll)
      --function <FUNCTION>    The function to execute inside payload.dll (SayHello)
      --parameter <PARAMETER>  The parameter to pass to the function inside payload.dll (https://localhost:1337/)
      --output <OUTPUT>        The output file path (shellcode.bin)
      --flags <FLAGS>          The 0x0 flag will execute DllMain and any other flag will execute the function inside payload.dll (SayHello) [default: 1]
  -h, --help                   Print help
  -V, --version                Print version
```

- 使用示例

```
srdi.exe --loader reflective_loader.dll --payload payload.dll --function FuncName --parameter inj --flags 1 --output shellcode.bin
```

之后通过 shellcode 加载器进行自注入。



## 参考

https://github.com/knownsec/KCon/blob/master/2024/%E9%AB%98%E7%BA%A7%E6%81%B6%E6%84%8F%E8%BD%AF%E4%BB%B6%E5%BC%80%E5%8F%91%E4%B9%8BRDI%E7%9A%84%E8%BF%9B%E5%8C%96.pdf
https://github.com/timwhitez/Doge-sRDI
https://github.com/memN0ps/venom-rs
https://github.com/monoxgas/sRDI