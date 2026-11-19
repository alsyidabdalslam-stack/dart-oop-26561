# Dart OOP Assignment: Kigali Bus Card

**Name:** Alsayed Abdalsalam
**Student ID:** 26561

## My numbers
- D = 61, L = 1
- Starting balance = 1000 + (61 × 10) = 1610 RWF
- Bus fare = 200 + 61 = 261 RWF
- Student discount = 10 + 1 = 11%

## Output of main.dart
```
Error: name too short
Owner: Alsayed | Balance: 1610 RWF
Owner: Alsayed Abdalsalam | Balance: 1610 RWF
Error: top-up must be 500 to 50000 RWF
Topped up 2000 RWF
Paid 261 RWF
Paid 261 RWF
Owner: Alsayed Abdalsalam | Balance: 3088 RWF
Student discount: 28 RWF
Paid 233 RWF
Owner: Alsayed Abdalsalam | Balance: 1377 RWF
Student card: 11% off
```

## Part 1: Why no setter for balance?
Because anyone could write `card.balance = 999999` and give themselves free money. With no setter, the balance can only change through `topUp` (which checks the amount) and `pay` (which checks there is enough money). The rules are always enforced.

## Part 2: What does ~/ do?
`~/` is integer division: it divides and throws away the decimal part.
- `print(237 * 17 / 100);` prints `40.29` (a double, with decimals)
- `print(237 * 17 ~/ 100);` prints `40` (an int, decimals cut off)

We use `~/` because RWF amounts must be whole numbers.