# Expander

Expander is a proof generation backend for Polyhedra Network. It aims to support fast proof generation.

This is the *rust version* of the "core" repo.

And [here](./gkr/src/tests/gkr_correctness.rs) for an example on how to use the gkr lib.

This is a core repo for our prover, to write circuits on our prover, please visit [our compiler](https://github.com/PolyhedraZK/ExpanderCompilerCollection)

## Developer helper

We understand that the product is currently in development and may not be very user-friendly yet. We encourage developers to join our Telegram chat group for Q&A: https://t.me/+XEdEEknIdaI0YjEx

Additionally, please take a look at our circuit compiler: https://github.com/PolyhedraZK/ExpanderCompilerCollection

This compiler is your entry point for using our prover; the repository you have is primarily the core executor, not the developer frontend. Our product pipeline is as follows:

`Your circuit code -> Expander Compiler -> circuit.txt & witness.txt -> Expander-rs -> proof `

Please note that the witness generation process is not yet optimal, and we are actively working on improving it.

## AVX
We use AVX2 by default. On an x86 or a mac, you can simply do
```
RUSTFLAGS="-C target-cpu=native" cargo test --release --workspace
```
For some platforms, if you do not indicate `target-cpu=native` it may simulate avx2 instructions, rather than use it directly, and this will cause performance decrease.

Our code also supports `avx512`. This is not turned on by default. To use `avx512`
```
RUSTFLAGS="-C target-cpu=native -C target-feature=+avx512f" cargo test --release --workspace
```

## Environment Setup

Before executing setup, please make sure you read through the system requirements, and make sure your CPU is in the list.

```sh
cargo run --bin=dev-setup --release
```


## Benchmarks

**Make sure you include `RUSTFLAGS="-C target-cpu=native"` to allow platform specific accelerations.**

Command template:

```sh
RUSTFLAGS="-C target-cpu=native" cargo run --release --bin gkr -- -f [fr|m31ext3] -t [#threads] -s [keccak|poseidon]
```

Concretely if you are running on a 16 physical core CPU for Bn256 scalar field:

```sh
RUSTFLAGS="-C target-cpu=native" cargo run --release --bin gkr -- -f fr -t 16
```

## Correctness test

[Here](./tests/gkr_correctness.rs) we provide a test case for end-to-end proof generation and verification.
To check the correctness, run the follow standard Rust test command:

```sh
RUSTFLAGS="-C target-cpu=native" cargo test --release -- --nocapture
```

## CLI

Usage:

```sh
RUSTFLAGS="-C target-cpu=native" cargo run --bin expander-exec --release -- prove <input:circuit_file> <input:witness_file> <output:proof>
RUSTFLAGS="-C target-cpu=native" cargo run --bin expander-exec --release -- verify <input:circuit_file> <input:witness_file> <input:proof>
RUSTFLAGS="-C target-cpu=native" cargo run --bin expander-exec --release -- serve <input:circuit_file> <input:ip> <input:port>
```

Example:

```sh
RUSTFLAGS="-C target-cpu=native" mpiexec -n 1 cargo run --bin expander-exec --release -- prove ./data/circuit_m31.txt ./data/witness_m31.txt ./data/out_m31.bin
RUSTFLAGS="-C target-cpu=native" mpiexec -n 1 cargo run --bin expander-exec --release -- verify ./data/circuit_m31.txt ./data/witness_m31.txt ./data/out_m31.bin
RUSTFLAGS="-C target-cpu=native" mpiexec -n 1 cargo run --bin expander-exec --release -- serve ./data/circuit_m31.txt 127.0.0.1 3030
```

To test the service started by `expander-exec serve`, you can use the following command:
```sh
python ./scripts/test_http.py  # need "requests" package
```

## Profiling
To get more fine-grained information about the running time, you can enable the `gkr/profile` feature, i.e.

```sh
RUSTFLAGS="-C target-cpu=native" cargo run --bin expander-exec --release --features gkr/profile -- prove ./data/circuit_m31.txt ./data/witness_m31.txt ./data/out_m31.bin
```

Note that enabling the `profile` feature will slightly reduce the overall performance so it is recommended not to enable it when benchmarking.

## How to contribute?

Thank you for your interest in contributing to our project! We seek contributors with a robust background in cryptography and programming, aiming to improve and expand the capabilities of our proof generation system.
