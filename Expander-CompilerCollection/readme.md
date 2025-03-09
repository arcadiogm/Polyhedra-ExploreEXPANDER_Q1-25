# ExpanderCompilerCollection

Expander is a proof generation backend for the Polyhedra Network. 
The ExpanderCompilerCollection - ECC is a component of the Expander proof system. It transforms circuits written in [gnark](https://github.com/Consensys/gnark) into an intermediate representation (IR) of a layered circuit. This IR can later be used by the [Expander prover](https://github.com/PolyhedraZK/Expander) to generate proofs.

## Documentation

Documentation at [Expander Compiler Collection Documentation](https://polyhedrazk.github.io/ExpanderDocs/).

## Using RUST this Library

[Rust frontend](https://polyhedrazk.github.io/ExpanderDocs/docs/rust/intro) RUST Library.

## Example 

Refer to [this example](https://polyhedrazk.github.io/ExpanderDocs/docs/go/example) for a practical demonstration of our compiler. In this example, we illustrate how a gnark circuit can be compiled using `ExpanderCompilerCollection`. The output of this example includes a circuit description file `"circuit.txt"` and a corresponding witnesses file `"witness.txt"`. Our prover, [Expander](https://github.com/PolyhedraZK/Expander), utilizes these IRs to generate the actual proof.
