# ATM Cash Dispenser — Chain of Responsibility (Java)

A compact Java demo of the Chain of Responsibility design pattern implemented as an ATM cash dispenser. The program models a chain of currency dispensers (1000, 500, 200, 100, 50, 20) that cooperate to fulfill a withdrawal request with the correct combination of bills.

Features
--------
- Clean, focused example of the Chain of Responsibility pattern.
- Single-class-per-file Java layout for easy exploration and modification.
- Example runner `BPI_Atm` demonstrating how the chain is constructed and used.

Why this project
-----------------
This repository is a teaching-quality example for software engineering classes or interview practice. It shows how to:

- Decouple request senders from handlers.
- Compose handler chains at runtime.
- Make adding new denominations straightforward with minimal code changes.

Quick Start
-----------
Requirements: Java 11+ (or any modern JDK).

Compile and run from the project root:

```bash
javac *.java
java BPI_Atm
```

You can also run a single example by calling the main class that builds the chain and issues withdrawals.

Repository Layout
---------------
- `BPI_Atm.java` — Example runner that assembles the chain and performs withdrawals.
- `ATMDispenseChain.java` — Helper that constructs the full chain of dispensers.
- `DispenseChain.java` — Interface / abstract handler defining the contract for dispensers.
- `Currency.java` — Simple value object representing an amount to dispense.
- `Peso1000Dispenser.java`, `Peso500Dispenser.java`, `Peso200Dispenser.java`, `Peso100Dispenser.java`, `Peso50Dispenser.java`, `Peso20Dispenser.java` — Concrete handlers for each denomination.

Design Overview
---------------
The chain is composed of handler objects. Each handler:

- Checks if it can handle part (or all) of the request based on its denomination.
- If it can, it dispenses the appropriate number of bills and forwards any remainder to the next handler.
- If it cannot, it passes the request onward unchanged.

ASCII Diagram
-------------

```
[BPI_Atm] -> [ATMDispenseChain] -> [Peso1000] -> [Peso500] -> [Peso200] -> [Peso100] -> [Peso50] -> [Peso20] -> null
```

Usage Example
-------------
After compiling, running `java BPI_Atm` should produce output similar to:

```
Requested amount: 3780
Dispensing 3 x 1000
Dispensing 1 x 500
Dispensing 1 x 200
Dispensing 0 x 100
Dispensing 1 x 50
Dispensing 1 x 20
Done.
```

Notes & Extension Ideas
-----------------------
- Add support for different currencies by introducing a factory that builds chains per currency.
- Add logging or metrics to see how often each denomination is used.
- Add validation to handle unavailable denominations or minimum/maximum withdrawal limits.

Contributing
------------
This is a small educational repo — feel free to open issues or submit pull requests that improve documentation, tests, or add new features.

License
-------
Reuse this code for learning or teaching. No license specified.

Enjoy exploring the Chain of Responsibility pattern!
