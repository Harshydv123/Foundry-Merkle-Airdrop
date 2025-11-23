✅ Merkle Airdrop – Foundry Project

A complete Foundry-based implementation of a secure Merkle Tree Airdrop with:
```
✅ ERC20 token distribution
✅ Merkle proof verification
✅ EIP-712 typed signatures
✅ Claim-once protection
✅ Full deployment scripts
✅ Unit tests
✅ Utilities for generating Merkle tree + proofs
```
📌 Project Overview

This project demonstrates how to distribute tokens to eligible users without storing a large on-chain whitelist, using:

🔹 Merkle Trees

Users prove inclusion with a Merkle proof.

🔹 EIP-712 Signatures

Prevents unauthorized claims and replay attacks.

🔹 SafeERC20

Ensures secure token transfers.

🧱 Tech Stack
```
Component	Used For
Foundry	Development, testing, fuzzing
Solidity 0.8.24	Smart contracts
OpenZeppelin Libraries	MerkleProof, SafeERC20, ECDSA
EIP-712	Typed message signing
Forge Scripts	Deployment + interaction
JSON proof files	Off-chain Merkle generation
```
```
📂 Folder Structure
├─ src/
│   ├─ MerkleAirdrop.sol
│   └─ BagelToken.sol
├─ script/
│   ├─ DeployMerkleAirdrop.s.sol
│   ├─ MakeMerkle.s.sol
│   ├─ SplitSignature.s.sol
│   ├─ Interact.s.sol
├─ out/
│   ├─ input.json
│   └─ output.json
├─ test/
│   └─ Unit/
│       └─ MerkleAirdrop.t.sol
├─ lib/
├─ foundry.toml
└─ README.md
```
🚀 Setup Instructions
1️⃣ Install Foundry
```
curl -L https://foundry.paradigm.xyz | bash
foundryup
```
2️⃣ Install dependencies
```
forge install
```
3️⃣ Build
```
forge build
```
4️⃣ Run tests
```
forge test -vvv
```
🔑 Generating Merkle Tree & Proofs
```
forge script script/MakeMerkle.s.sol
```

Output includes:
```
input.json
output.json
```
📜 Deploying the Contract
Deploy token + airdrop
```
forge script script/DeployMerkleAirdrop.s.sol --broadcast
```
Interact with deployment
```
forge script script/Interact.s.sol
```
🧪 Running Tests
```
forge test -vvv
```
🧠 Example Solidity Claim Test Snippet
```
function testUsersCanClaim() public {
    uint256 startingBalance = token.balanceOf(user);

    vm.startPrank(user);
    (uint8 v, bytes32 r, bytes32 s) = signMessage(user, amountToCollect);
    vm.stopPrank();

    vm.prank(gasPayer);
    airdrop.claim(user, amountToCollect, proof, v, r, s);

    uint256 endingBalance = token.balanceOf(user);
    assertEq(endingBalance - startingBalance, amountToCollect);
}
```
🔐 Security Considerations
```
✅ Prevents double-claiming
✅ Protects against forged signatures
✅ Uses SafeERC20 for safety
✅ Merkle root cannot be modified
```
🧭 Learning Value for Security Researchers

By reading this repo you learn:
```
✅ Merkle tree whitelist patterns
✅ EIP-712 typed data hashing
✅ Signature replay prevention
✅ Claim authorization models
✅ Airdrop attack surfaces
```
⭐ Contributing

Pull requests welcome — especially:

✅ fuzz tests
✅ invariant tests
✅ signature phishing examples

📝 License

MIT License — free to use & modify.

🙌 Author

Built by Harsh while learning secure and professional airdrop architecture in Foundry.
