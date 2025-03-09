# Building zkML with GKR Protocol



## Defi Lending and Borrowing

> Decentralized lending/borrowing is implemented through Smart Contracts that let users LEND or BORROW digital assets at fixed or variable interest rates.

### ORACLEs Integration:

Oracles serve as the data bridges for DeFi applications, enabling Smart Contracts to interact with external data sources, and they provide this information by fetching data from multiple trusted sources and delivering it to the blockchain.

Oracles provide accurate and real-time: price feeds for assets, interest rates and collateral values, among others.

## Typical Workflow

. Implement the circuit in RUST circuit frontend language.

. Use ExpanderCompilerCollection - ECC to compiler the circuit into layered circuit.

. Use Expander PROVER to generate and verify proofs.

### Process workflow – Detailed steps
#### Pre-Processing stage

0 . Synthetic Data generator

1 . ML model -> Find and Train an ML model PyTorch

2 . Export the ML model to ONNX - Open Neural Network Exchange

3 . Convert to ZK Circuit -> Use ECC - Expander Compiler Collection

#### Runtime stage

4 . ZK circuit – Expander Prover -> Generate a circuit with a proof a prediction

5 . Smart contract to validate on-chain

6 . Proof storage EXPchain



