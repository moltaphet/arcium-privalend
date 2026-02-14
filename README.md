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
Assets are converted into a confidential data type: `SecretU64`. Not even the protocol admins can see the user's exact balance.

### 2. Confidential Credit Scoring
Arcium nodes extract the user's credit history as a `SecretU16` directly from their past on-chain behavior without decrypting it.

### 3. The MPC Magic (Confidential Computation)
The Arcium network nodes perform calculations within a **Secure Enclave**.
* **The Formula**: 
  $$Borrowing Power = Collateral + (Credit Score \times 20)$$

### 4. Verification & Signal
If the $Borrowing Power \ge Loan Request$, an approval signal is generated via `.reveal()` to notify the Solana program.

### 5. On-chain Settlement
The Solana program receives the signal and triggers the loan disbursement while keeping raw data hidden.

---

## 🛠 Tech Stack
* **Language**: Rust 🦀
* **Blockchain**: Solana
* **Privacy Layer**: Arcium MPC Network

---

## 🧪 How to Test the MPC Logic
To ensure the confidential computation is functioning correctly, run the built-in test suite:

```bash
cargo test -- --nocapture
```
1. What is being tested?The test verifies the Confidential Borrowing Power formula ($Collateral + Credit Score \times 20$) to ensure the weighted lending logic is intact.

2. Expected Output

```bash
test tests::test_confidential_logic ... ok
test result: ok. 1 passed; 0 failed; 0 ignored;
```