# ExpanderCompilerCollection - ECC

Expander is a proof generation backend for the Polyhedra Network. 

The ExpanderCompilerCollection (ECC) is a component of the Expander proof system. It transforms circuits written in RUST language into an Intermediate Representation (IR) of a layered circuit. This IR can later be used by the [Expander prover](https://github.com/PolyhedraZK/Expander) to generate proofs.

## Using ECC Library

To incorporate the compiler into RUST project, include the following import statement in your code:

We also have a [Rust frontend](https://polyhedrazk.github.io/ExpanderDocs/docs/rust/intro) similar to gnark.

## Example 

Refer to [this example](https://polyhedrazk.github.io/ExpanderDocs/docs/go/example) for a practical demonstration of our compiler. In this example, we illustrate how a gnark circuit can be compiled using `ExpanderCompilerCollection`. The output of this example includes a circuit description file `"circuit.txt"` and a corresponding witnesses file `"witness.txt"`. Our prover, [Expander](https://github.com/PolyhedraZK/Expander), utilizes these IRs to generate the actual proof.
