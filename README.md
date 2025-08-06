# 🗳 VeriVote – Decentralized Governance Framework

**VeriVote** is a Clarity-based smart contract for enabling decentralized, transparent, and flexible protocol governance. Built to empower token holders, VeriVote facilitates the creation, voting, and execution of proposals on-chain — ensuring community-led protocol evolution with auditable decision-making.

---

## ✨ Key Features

* **Proposal Lifecycle**
  Token holders can create proposals to change protocol parameters, execute contract calls, allocate funds, or initiate upgrades.

* **On-Chain Voting**
  Every vote is recorded transparently on the blockchain. Support includes `for`, `against`, and `abstain` options with rationale notes.

* **Delegated Voting**
  Token holders can delegate their voting power to trusted representatives while maintaining full control to revoke at any time.

* **Customizable Parameters**
  Parameters like quorum thresholds, majority requirements, execution delays, and deposit amounts are all adjustable through governance.

* **Secure Execution**
  Proposals marked as "passed" are executed only after a defined delay, and actions are validated to prevent misuse.

* **Snapshot Voting**
  Voting power is determined based on token balances at the start of the voting period, ensuring fairness and preventing manipulation.

---

## 🔐 Contract Components

### 1. `protocol-parameters`

A map storing key-value pairs representing modifiable system parameters such as quorum, delay, and treasury address.

### 2. `proposals`

Tracks all proposals, including metadata (title, description, proposer, timestamps) and status (`draft`, `active`, `passed`, etc.).

### 3. `proposal-actions`

Defines the actions to be executed if a proposal passes: update parameters, transfer funds, or make contract calls.

### 4. `votes`

Stores voting records per proposal and voter, along with vote type, weight, timestamp, and optional rationale.

### 5. `vote-delegations`

Allows a user to delegate voting rights to another address for increased convenience and representation.

---

## 🧠 How It Works

1. **Initialization**
   Admin initializes core protocol parameters using the `initialize-parameters` function.

2. **Proposal Creation**
   Eligible users can create proposals after staking a minimum deposit using `create-proposal`.

3. **Action Definition**
   Proposal authors attach executable actions via `add-proposal-action`.

4. **Activation & Voting**
   Proposals are activated and open for voting using `activate-proposal`, then token holders vote via `cast-vote`.

5. **Finalization & Execution**
   After the voting period and execution delay, proposals are finalized with `finalize-proposal` and executed with `execute-proposal`.

---

## 🛠 Functions Overview

| Function                                    | Type      | Description                                 |
| ------------------------------------------- | --------- | ------------------------------------------- |
| `initialize-parameters`                     | Public    | Sets default system-wide parameters         |
| `create-proposal`                           | Public    | Allows token holders to initiate a proposal |
| `add-proposal-action`                       | Public    | Adds actions to an existing proposal        |
| `activate-proposal`                         | Public    | Moves a proposal to the voting phase        |
| `cast-vote`                                 | Public    | Allows a user (or their delegate) to vote   |
| `finalize-proposal`                         | Public    | Tallies votes and updates proposal status   |
| `execute-proposal`                          | Public    | Executes proposal actions post-delay        |
| `delegate-votes`                            | Public    | Delegates a user's voting power             |
| `remove-delegation`                         | Public    | Revokes delegated authority                 |
| `get-proposal`, `get-parameter`, `get-vote` | Read-Only | Retrieves on-chain records                  |

---

## 🧪 Example Parameters

| Name               | Value        | Description                                |
| ------------------ | ------------ | ------------------------------------------ |
| `voting-delay`     | 1440 blocks  | Delay between proposal creation and voting |
| `voting-period`    | 10080 blocks | Duration of the voting window              |
| `execution-delay`  | 2880 blocks  | Time between passing and execution         |
| `quorum-threshold` | 1000 (10%)   | Minimum participation                      |
| `super-majority`   | 6000 (60%)   | Threshold for critical decisions           |

---

## 📦 Integration

* **Governance Token**: Must implement the [SIP-010 FT Standard](https://github.com/stacksgov/sips/blob/main/sips/sip-010/sip-010-ft-standard.md)
* **Snapshot Support**: Currently uses live balance. Consider integrating a snapshot system for production use.

---

## 🔒 Security Notes

* Only proposals with quorum and majority thresholds are executed.
* Delegation is optional and revocable.
* System parameters can only be changed via governance.
* `execute-proposal-actions` should be extended for full action handling.

---

## 📜 License

MIT License – Use freely, improve collaboratively.

---

## 👥 Credits

Built using the Clarity smart contract language for the Stacks blockchain.
Designed with decentralized communities and DAOs in mind.