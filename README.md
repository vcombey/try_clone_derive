Try Clone Derive.rs
==============

A crate wich add a derive TryClone macro for the TryClone Trait of the fallible_allocation crate

## Limitation
This is my first proc macro, the code is very dummy and works only
on the simplest cases, without Generic types, etc
But contributions are welcome !

# Getting Started

[try clone derive is available on crates.io](https://crates.io/crates/try_clone_derive).
It is recommended to look there for the newest released version, as well as links to the newest builds of the docs.

At the point of the last update of this README, the latest published version could be used like this:

Add the following dependency to your Cargo manifest...

```toml
[dependencies]
try_clone_derive = "0.1.0"
```

...and see the [docs](https://docs.rs/try_clone_derive) for how to use it.

# Example

```rust
use fallible_collections::TryClone;

use try_clone_derive::TryClone;

#[derive(Debug, TryClone)]
pub struct MyStruct{
    a: u32,
    b: Vec<u8>,
    c: Arc<u8>,
}

fn main() {
	// this crate an Ordinary box but return an error on allocation failure
	let my_struct = MyStruct {
		a: 42,
		b: vec![42; 42],
		c: Arc::new(42),
	};
	assert_eq!(my_struct.try_clone().unwrap(), my_struct);
}
```

## License

Licensed under either of

 * Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be dual licensed as above, without any
additional terms or conditions.
