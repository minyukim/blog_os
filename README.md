# Blog OS

My own learning journey of writing a tiny OS in Rust (https://os.phil-opp.com/).
With about 3 years of experience of firmware development in C, I'm trying to see how Rust can bring the modern software engineering practices to the low-level system programming world.

## Key takeaways

- Rust's built in package manager (cargo) and powerful type system make it easy to design and use modules in system programming world.
  - [Cargo.toml](Cargo.toml) acts as a single source of truth for dependencies and build configuration.
  - The type system acts as a strong contract, making it hard to make mistakes in using modules.

- The bootloader expects the entry point to be a C ABI (extern "C"). There is no ABI in Rust yet (https://github.com/rust-lang/rfcs/issues/600).

- The [conditional compilation (`#[cfg(..)]` and `#[cfg_attr(..)]`)](https://doc.rust-lang.org/reference/conditional-compilation.html) is much easier to use and harder to make mistakes than the C macros.

- There are a lot of ways to implement a memory allocator. The [blog](https://os.phil-opp.com/allocator-designs/) mentions some allocator designs such as
  - Bump allocator
  - Arena allocator
  - Linked list allocator
  - Fixed-size block allocator
  - Page allocator
  - Slab allocator
  - Buddy allocator


## Differences from the blog

- Use [rust-toolchain.toml](rust-toolchain.toml) to manage toolchain declaratively (https://rust-lang.github.io/rustup/overrides.html#the-toolchain-file).
- Use specific nightly version (2025-06-04) to avoid regressions and breaking changes (there is a [regression on x86-interrupt ABI in nightly 1.90.0](https://github.com/rust-lang/rust/issues/143072)).

## Try it out

### Prerequisites

- [rustup](https://rustup.rs/)
- [qemu](https://www.qemu.org/)
- [bootimage](https://github.com/rust-osdev/bootimage)

### Run

```
cargo run
```

### Test

```
cargo test
```