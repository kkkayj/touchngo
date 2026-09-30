# TNG eWallet Simulator

LDCW6123 Group Project – Part 2: Interactive C++ Program

This program is linked to our Part 1 poster on **Touch 'n Go**, analysed with Clayton
Christensen's Disruptive Innovation Model. Touch 'n Go grew from a toll card (1997) into
an eWallet (2018) that also pays highway tolls through RFID (2019). The program simulates
those eWallet actions in the terminal.

## Menu

```
1. Check balance
2. Reload
3. Pay toll (RFID)
4. Exit
```

The menu repeats after every action until the user chooses 4 (Exit).

## Inputs and outputs

| Option | User enters | Program shows |
|---|---|---|
| 1. Check balance | nothing | the current balance, e.g. `Your balance: RM25.00` |
| 2. Reload | an amount in RM, e.g. `50` | the new balance, or why the reload was refused |
| 3. Pay toll (RFID) | a vehicle class: 1 car, 2 small lorry, 3 large lorry | the toll paid and the new balance, or why it was refused |
| 4. Exit | nothing | a thank-you message with the final balance |

## Rules (example values for this simulation, not official Touch 'n Go limits)

- The wallet starts at **RM0.00**.
- The minimum reload is **RM10.00**.
- The balance can never go above **RM1,500.00** (wallet limit).
- Toll fares: Class 1 **RM2.50**, Class 2 **RM5.00**, Class 3 **RM7.50**
  (example flat fares; real fares depend on the toll plaza).
- A toll is refused if the balance is too low.

## Errors the program handles

| Situation | Message |
|---|---|
| Menu option that isn't 1–4, or letters | `Invalid option - please choose 1 to 4.` |
| Reload below RM10, negative, or letters | `Minimum reload is RM10.00. Reload cancelled.` |
| Reload that would pass RM1,500 | `Wallet limit is RM1500.00. You can reload up to RM... more.` |
| Vehicle class that isn't 1–3, or letters | `No such vehicle class. Toll not paid.` |
| Toll costs more than the balance | `Insufficient balance (RM...) for RM... toll. Please reload first.` |

## Program logic

- A `while` loop keeps showing the menu until the choice is 4.
- A `switch` on the menu choice runs the matching option.
- `if / else if / else` checks each rule (minimum reload, wallet limit, enough balance).
- A second `switch` sets the toll fare from the vehicle class.
