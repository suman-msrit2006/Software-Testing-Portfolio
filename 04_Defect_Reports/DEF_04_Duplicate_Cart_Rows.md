# DEF-04: Adding the same item and option again creates a duplicate cart row

| Field | Details |
|-------|---------|
| Defect ID | DEF-04 |
| Module | Cart |
| Application | BlissBite (localhost:3000) |
| Related test cases | CT_04 (and possibly CT_06) |
| Reported by | <name of the person who ran CT_04> |
| Date | 18-11-2026 |
| Severity | Minor |
| Priority | Medium |
| Status | Open |

## Description
When an item that is already in the cart is added again with the same quantity option and portion, the cart shows a separate second row for it instead of merging the two into one row with the quantities and amounts added together.

## Steps to reproduce
1. Log in as rahul.sharma@test.com and open http://localhost:3000 with an empty cart.
2. Add Veg Fried Rice, quantity 1, half (110) to the cart.
3. Add Veg Fried Rice, quantity 1, half to the cart again.
4. Open the cart.

## Expected result
One Veg Fried Rice half row with quantity 2 and amount 220.

## Actual result
Two separate Veg Fried Rice half rows, each with quantity 1 and amount 110. The total price is still the correct sum.

## Impact
The cart is cluttered with duplicate rows, and the same duplicates would be sent into the order. Prices are not affected.

## Environment
Windows, Google Chrome (Brave), BlissBite running locally (frontend port 3000, backend port 5000)

## Evidence
- 07_Screenshots/Cart/CT_05_different_option.png (cart before the second add)
- 07_Screenshots/Cart/CT_04_same_item_twice.png
