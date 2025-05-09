[![crates.io](https://img.shields.io/crates/v/rustsat-ipasir?style=for-the-badge&logo=rust)](https://crates.io/crates/rustsat-ipasir)
[![docs.rs](https://img.shields.io/docsrs/rustsat-ipasir?style=for-the-badge&logo=docsdotrs)](https://docs.rs/rustsat-ipasir)
[![License](https://img.shields.io/crates/l/rustsat-cadical?style=for-the-badge)](../LICENSE)

<!-- cargo-rdme start -->

# rustsat-ipasir - IPASIR Bindings for RustSAT

[IPASIR](https://github.com/biotomas/ipasir) is a general incremental interface for SAT
solvers. This crate provides bindings for this API to be used with the
[RustSAT](https://github.com/chrjabs/rustsat) library.

**Note**: This crate only provides bindings to the API, linking to a IPASIR library needs to be
set up by the user. This is intentional to allow easy integration of solvers that we do not
provide a specialized crate for. For a plug-and-play experience see the other RustSAT solver
crates.

## Linking

Linking to a IPASIR library can be done by adding something like the following to your projects
build script (`build.rs`).

```rust
// Link to custom IPASIR solver
// Modify this for linking to your static library
// The name of the library should be _without_ the prefix 'lib' and the suffix '.a'
println!("cargo:rustc-link-lib=static=<path-to-your-static-lib>");
println!("cargo:rustc-link-search=<name-of-your-static-lib>");
// If your IPASIR solver links to the C++ stdlib, the next four lines are required
#[cfg(target_os = "macos")]
println!("cargo:rustc-flags=-l dylib=c++");
#[cfg(not(target_os = "macos"))]
println!("cargo:rustc-flags=-l dylib=stdc++");
```

## Minimum Supported Rust Version (MSRV)

Currently, the MSRV is 1.76.0, the plan is to always support an MSRV that is at least a year
old.

Bumps in the MSRV will _not_ be considered breaking changes. If you need a specific MSRV, make
sure to pin a precise version of RustSAT.

<!-- cargo-rdme end -->
