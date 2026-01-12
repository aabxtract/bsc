BNB Smart Chain (BSC)

BNB Smart Chain (BSC) is an EVM-compatible blockchain designed to bring programmability, interoperability, and high-performance execution to the BNB ecosystem.

Its primary objective is to extend the capabilities of BNB Beacon Chain by enabling smart contracts and decentralized applications, while maintaining compatibility with the Ethereum ecosystem and its extensive tooling.

🎯 Design Philosophy

To leverage the maturity and adoption of Ethereum’s developer ecosystem, BNB Smart Chain is implemented as a fork of go-ethereum (Geth). This approach ensures:

Compatibility with existing Ethereum smart contracts

Seamless use of Ethereum developer tooling

Faster adoption and reduced migration overhead

BNB Smart Chain deeply respects the engineering foundations of Ethereum, and builds upon them to introduce performance and governance optimizations.

As a result, many binaries, tools, and documentation references retain Ethereum-based naming conventions (e.g., geth).

📚 Resources

API Reference

Build & Test

Community: Discord

🧱 Core Architecture

While retaining full EVM compatibility, BNB Smart Chain introduces a distinct consensus and validator model to optimize performance and cost.

Key Enhancements

21 Validators

Proof of Staked Authority (PoSA) consensus

Short block times

Lower transaction fees

Fast finality

Validators are elected from bonded validator candidates based on staking weight. Security and stability are enforced through:

Double-sign detection

Slashing mechanisms

On-chain validator rotation

🔑 Key Properties

BNB Smart Chain is designed to be:

Self-sovereign
Secured by a validator set elected through staking.

EVM-Compatible
Supports Ethereum tooling with improved throughput and lower fees.

Governed On-Chain
PoSA enables decentralization through community participation.
BNB serves as both the staking token and the gas token for execution.

For a deeper technical overview, refer to the BNB Smart Chain Whitepaper.

🚀 Release Types

BSC follows a structured release strategy:

1. Stable Releases

Production-ready builds for general users.

Format:
v<Major>.<Minor>.<Patch>
Example: v1.5.19

2. Feature Releases

Early access builds introducing isolated features without affecting core stability.

Format:
v<Major>.<Minor>.<Patch>-feature-<FeatureName>
Example: v1.5.19-feature-SI

3. Preview Releases

Cutting-edge builds for testing and early feedback.

Format:
v<Major>.<Minor>.<Patch>-<Meta>
Meta values include alpha, beta, rc.

Example: v1.5.0-alpha

⚙ Consensus: Proof of Staked Authority (PoSA)

While Proof-of-Work (PoW) provides strong decentralization, it is resource-intensive and environmentally costly.

BNB Smart Chain introduces Proof of Staked Authority, combining the strengths of:

Proof of Authority (PoA) — efficiency and predictable block times

Delegated Proof of Stake (DPoS) — community governance and decentralization

Parlia Consensus Engine

BNB Smart Chain implements a custom consensus engine called Parlia, featuring:

A limited validator set producing blocks

Round-robin block production similar to Ethereum’s Clique

Validator election and rotation via staking-based governance

Integration with system contracts for:

Slashing

Rewards distribution

Validator set updates

🪙 Native Token

BNB functions as the native token on BNB Smart Chain, analogous to ETH on Ethereum.

BNB is used to:

Pay transaction and smart contract execution fees

Participate in staking and governance

🛠 Building from Source
Requirements

Go version 1.24+

C Compiler (GCC 5+)

Refer to the Installation Guide for prerequisites.

Build Commands
make geth


To build all utilities:

make all

CGO Build Issue Fix

If you encounter:

Caught SIGILL in blst_cgo_init


Rebuild with:

export CGO_CFLAGS="-O -D__BLST_PORTABLE__"
export CGO_CFLAGS_ALLOW="-O -D__BLST_PORTABLE__"

📦 Executables

The cmd/ directory provides the following tools:

Command	Description
geth	Main BNB Smart Chain client supporting full, archive, and light nodes with extensive RPC interfaces
clef	External transaction signing service
devp2p	Networking-layer utilities
abigen	Generates Go bindings from smart contract ABIs or Solidity
bootnode	Lightweight node discovery service
evm	Developer EVM for opcode-level debugging
rlpdump	RLP decoding utility
🖥 Hardware Requirements
Mainnet Full Node

SSD (≥ 3 TB, NVMe recommended)

16 CPU cores

64 GB RAM

≥ 5 MB/s network throughput

Recommended instances:

AWS: m5zn.6xlarge, r7iz.4xlarge

GCP: c2-standard-16

Testnet

500 GB storage

4 CPU cores

16 GB RAM

▶ Running a Full Node
1. Download Prebuilt Binary

(Linux / macOS examples omitted here for brevity)

2. Download Network Configuration

Mainnet

Testnet

3. Download Snapshot

Use the latest chain snapshot and follow the directory structure guide.

4. Start the Node
./geth --config ./config.toml --datadir ./node \
  --cache 8000 --rpc.allow-unprotected-txs \
  --history.transactions 0


High-performance option:

--tries-verify-mode none

5. Monitor Sync

Logs are available at:

./node/bsc.log

🔌 JSON-RPC Interfaces

Geth supports:

IPC (enabled by default)

HTTP

WebSocket

RPC endpoints must be explicitly enabled for HTTP and WS due to security risks.

⚠️ Security Warning:
Exposing RPC endpoints publicly can compromise node integrity. Always use network-level protections.

🌐 Private Networks & Bootnodes

BSC-Deploy: Network deployment tooling

Bootnodes: Lightweight discovery-only nodes

Production deployments should use full nodes as bootstrap peers rather than developer bootnodes.

🤝 Contributing

Contributions are welcome and appreciated.

Guidelines

Follow Go formatting (gofmt)

Use Go documentation standards

Base PRs on master

Prefix commit messages with affected packages

Example:

eth, rpc: make trace configs optional


For large changes, consult core developers via Discord before submitting.

📄 License

Library code: GNU LGPL v3.0 (COPYING.LESSER)

Binaries: GNU GPL v3.0 (COPYING)

ℹ About

BNB Smart Chain is a high-performance, EVM-compatible blockchain built as a fork of go-ethereum, optimized for scalability, governance, and cost efficiency.
