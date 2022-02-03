# Hooks
Hooks are small, efficient web assembly modules designed specifically for the XRP Ledger. Hooks can be written in any language (compilable to WebAssembly), most business logic and most smart contract concepts can be implemented in a hook. Typically Hooks are written in C.

Hooks are set onto an account using a `SetHook` transaction and once installed on an account, a hook can:
1. Block or allow incoming and outgoing transactions on the account
2. Modify and maintain internal state and logic specific to the hook on that account
3. Emit new transactions on behalf of the account

## Glossary

This Hooks documentation is highly technical and the Hooks API use a set of unfamiliar terms.
| Term | Description |
| --- | --- |
| Hook | This term refers to a range of things depending on the context <br />1. A webassembly binary uploadable to the XRPL with the SetHook Transaction type. <br />2. A webassembly binary already uploaded to and set or configured onto an XRPL account. <br />3. The source code of such a binary. |
| Hook Account | The account where the currently executing Hook lives. This is the account that owns the Hook, the account that performed the SetHook Transaction which created the Hook and the account to whom belongs the Hook State for the currently executing Hook. |
| Emitted Transaction | A new transaction created by a Hook during the Hook's execution that is not the Originating Transaction. These are typically used for sending funds back to the Originating Account. See: Emitted Transactions. |
| Originating Transaction | The transaction that triggered the Hook to fire. This could be either a transaction sent out of or into an account with a Hook set on it. |
| Originating Account | The account that sent an Originating Transaction. |
| Hook State | A per-account key-value map of 32 byte keys to arbitrary data. All Hooks present on an account have access to the same Hook State and can modify it. Note that the Hook State lives on the Hook Account not on the Originating Account. See: State Management. |
| SetHook | A new Transaction Type introduced in the Hooks ammendment which sets a Hook onto an XRPL account. See: SetHook Transaction. |
| Guards | A special control mechanism you need to use if you write a loop into in a Hook. See: Loops and Guarding. |
| XFL or Floating Point | A way to do high precision math in Hooks such as for exchange rate computation. See: Floating Point Numbers (XFL). |
| Serialized Objects (STO)| The way xrpld transmits and stores ledger objects. See: Serialized Objects. |
| Slots and Keylets | Slots can contain ledger objects and keylets identify those objects. See: Slots and Keylets. |
| Trace | A way to print a log line to the xrpld output from a Hook. See: Debugging Hooks. |
