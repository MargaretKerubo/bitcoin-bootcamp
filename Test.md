# Bitcoin Core Exercise — Verification Test

## Objective

Verify that the participant successfully:
- Created two wallets
- Generated addresses
- Funded a wallet
- Sent a transaction
- Verified balances

---

## Submission Requirements

Submit a single file named:

submission.md

Include:
1. Commands executed
2. Terminal output after each command
3. Final balances

Commands and outputs should appear in order.

---

## Required Steps

### Step 1 — Create Wallets

Run:

```bash
bitcoin-cli -regtest createwallet "alice"
bitcoin-cli -regtest createwallet "bob"
```

Expected:
- Both wallets created or loaded.

---

### Step 2 — Generate Addresses

Run:

```bash
bitcoin-cli -regtest -rpcwallet=alice getnewaddress
bitcoin-cli -regtest -rpcwallet=bob getnewaddress
```

Expected:
- Two valid regtest addresses.

Record both.

---

### Step 3 — Fund Alice

Mine blocks:

```bash
bitcoin-cli -regtest -rpcwallet=alice generatetoaddress 101 <ALICE_ADDRESS>
```

Check balance:

```bash
bitcoin-cli -regtest -rpcwallet=alice getbalance
```

Expected:
- Balance > 0 BTC

---

### Step 4 — Send Transaction

Send 5 BTC from Alice to Bob:

```bash
bitcoin-cli -regtest -rpcwallet=alice sendtoaddress <BOB_ADDRESS> 5
```

Mine one block:

```bash
bitcoin-cli -regtest -rpcwallet=alice generatetoaddress 1 <ALICE_ADDRESS>
```

Expected:
- Transaction confirmed

---

### Step 5 — Verify Balances

Run:

```bash
bitcoin-cli -regtest -rpcwallet=alice getbalance
bitcoin-cli -regtest -rpcwallet=bob getbalance
```

Expected:
- Bob balance ≥ 5 BTC

---

## Pass Conditions

PASS if:

- Wallets exist
- Addresses generated
- Alice mined successfully
- Transaction completed
- Bob received funds

FAIL if:

- Missing outputs
- Incorrect sequence
- Transaction not confirmed

---

Good luck 🚀
