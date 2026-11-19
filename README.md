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

## Part 4: Bug table
| Bug | The line | Why it is wrong (your words) | Your fix |
|-----|----------|------------------------------|----------|
| 1 | `String _brand;` and `int _battery;` | The fields have no starting value, and Dart does not allow that for non-nullable fields | `String _brand = '';` and `int _battery = 0;` |
| 2 | `SmartPhone(String brand, int battery, String system) {` | The constructor does not call the parent constructor, but Phone needs brand and battery | Add `: super(brand, battery)` |
| 3 | `@override void restart()` | `@override` only works if the parent has that method, and Phone has no `restart` | Remove `@override` |
| 4 | `p.battery = 100;` | There is a getter but no setter for battery | Add `set battery(int value)` that accepts only 0 to 100 |
| 5 | `print(p.battery());` | `battery` is a getter, not a method, so it must not have `()` | `print(p.battery);` |
| Not a bug | `Phone p = new Phone('Tecno', 50);` | `new` is the old style but it is still valid in Dart, so the code works | (none) |


## Part 5
My prediction:
```
1
5
```
Why: `a.add()` makes items 1. `a.items = -5` is refused by the setter because -5 is below 0, so it stays 1 and the first print shows 1. For `BigBag`, `add()` calls `super.add()` twice, so each `b.add()` adds 2. After two calls items is 4. Then `b.items = b.items + 1` makes it 5, and the setter accepts it.