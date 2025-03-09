# Building zkML with GKR Protocol

## Defi Lending and Borrowing

> Decentralized lending/borrowing is implemented through Smart Contracts that let users LEND or BORROW digital assets at fixed or variable interest rates.

### ORACLEs Integration:

Oracles serve as the data bridges for DeFi applications, enabling Smart Contracts to interact with external data sources, and they provide this information by fetching data from multiple trusted sources and delivering it to the blockchain.

Oracles provide accurate and real-time: price feeds for assets, interest rates and collateral values, among others.

### Process workflow – Detailed steps
#### Pre-Processing stage

0 . Synthetic Data generator

1 . ML model -> Find and Train an ML model PyTorch

2 . Export the ML model to ONNX - Open Neural Network Exchange

3 . Convert to ZK Circuit -> Use ECC - Expander Compiler Collection

#### Runtime stage

4 . ZK cir	cuit – Expander Prover -> Generate a circuit with a proof a prediction

5 . Smart contract to validate on-chain

6 . Proof storage EXPchain



