# PasswordStore Contract Audit

This repository contains the audit report for the **PasswordStore smart contract**, prepared by **0xSnowEth**. The report includes details about the smart contract's security, potential vulnerabilities, and suggested improvements.

---

## Overview

**PasswordStore** is a smart contract that allows a user to store and retrieve a password on the blockchain. The contract is intended to be used by a single owner, who can set and access the stored password.

---

### High-Risk Findings:
- **Passwords stored on-chain are visible to anyone**, regardless of Solidity variable visibility.
- The **setPassword function** can be called by anyone, allowing unauthorized users to change the password.

### Low-Risk Findings:
- The contract has an **initialization timeframe vulnerability**, where the password is not set upon contract deployment, leaving it in an uninitialized state.

---

## Findings and Recommendations

### High-Risk Findings

#### **Passwords Stored On-Chain Are Visible to Anyone**

- **Issue**: The password is stored on-chain in plain text and can be read by anyone using off-chain tools.
- **Recommendation**: Encrypt the password off-chain before storing it on the blockchain to keep it private.

#### **setPassword Function Is Callable by Anyone**

- **Issue**: The setPassword function lacks access control, allowing anyone to change the password.
- **Recommendation**: Implement access control by adding a modifier to ensure only the contract owner can set the password.

### Low-Risk Findings

#### **Initialization Timeframe Vulnerability**

- **Issue**: The password is not set during contract deployment, which leaves it uninitialized and vulnerable during the initialization period.
- **Recommendation**: Set an initial password during contract construction to mitigate this risk.

---

## Tools Used

- Manual inspection of the contract's code.
- **Foundry** for reading contract storage off-chain.

---

### License

This project is licensed under the **MIT License**.

*Audited by [0xSnowEth](https://x.com/0xSnowEth)*


