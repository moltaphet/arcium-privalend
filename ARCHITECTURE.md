PrivaLend Visual Workflow

1. User Side: Connects Phantom Wallet, inputs loan amount (e.g., 500 USDC).

2. Privacy Layer: Arcium SDK encrypts the input into a SecretU64.

3. MPC Processing: 3 Nodes calculate the credit-to-collateral ratio.

4. Result: Only the "Success/Fail" signal is sent back to Solana, keeping the user's balance private.

Step 1: User locks $1000$ USDC (Encrypted as SecretU64).
Step 2: The system fetches a SecretU16 credit score from past on-chain behavior.
Step 3: Arcium nodes perform: $BorrowingPower = Collateral + (Score \times 20)$.
Step 4: If $BorrowingPower > Request$, the loan is triggered on Solana.