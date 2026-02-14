# 🏦 PrivaLend: Confidential Lending & Borrowing

**PrivaLend** is a next-generation DeFi protocol built on **Solana**, powered by **Arcium's Multi-Party Computation (MPC)**. It enables users to access under-collateralized loans by evaluating their financial health through encrypted credit scores and private assets.

---

## 🔐 The Core Problem

In traditional DeFi, all collateral amounts and credit histories are public. This total transparency leads to:

1. **Privacy Risks**: Your entire net worth is visible on-chain.
2. **Capital Inefficiency**: Users must over-collateralize because their true creditworthiness is unknown.

---

## ⚙️ How PrivaLend Works (Step-by-Step)

### 1. Encrypted Input Phase

When a user requests a loan, their collateral amount is not stored as plaintext on the blockchain.

* **Technical Action**: Using the **Arcium SDK**, assets are converted into a confidential data type: `SecretU64`.
* **Result**: Not even the protocol admins can see the user's exact balance.

### 2. Confidential Credit Scoring

To enable under-collateralized loans, the system must verify the user's reputation without exposing it.

* **Technical Action**: Arcium nodes extract the user's credit history as a `SecretU16` directly from their past on-chain behavior without decrypting it.

### 3. The MPC Magic (Confidential Computation)

This is where the heavy lifting happens. The Arcium network nodes perform calculations within a **Secure Enclave**.

* **The Formula**:


* **Technical Action**: Nodes work with encrypted "shares" of the data. They collaborate to compute the result without any single node ever seeing the raw input values.

### 4. Verification & Signal

Once the computation is complete, the final output is a simple Boolean (Yes/No).

* **Technical Action**: If the , an approval signal is generated. This is the only part that is decrypted using `.reveal()` to notify the Solana program.

### 5. On-chain Settlement

The Solana program receives the "Success" signal and triggers the loan disbursement.

* **Final Outcome**: The loan is issued while the user's **exact assets** and **credit score** remain completely hidden throughout the entire lifecycle.

---

## 🛠 Tech Stack

* **Language**: Rust 🦀
* **Blockchain**: Solana
* **Privacy Layer**: Arcium MPC Network (Secret Types: `SecretU64`, `SecretU16`)
* **Serialization**: Borsh & Serde

---

## 🚀 Future Roadmap

* **Confidential Liquidations**: Triggering liquidations based on encrypted price feeds.
* **Cross-chain Private Credit**: Bringing credit scores from other chains into the Arcium enclave.

---