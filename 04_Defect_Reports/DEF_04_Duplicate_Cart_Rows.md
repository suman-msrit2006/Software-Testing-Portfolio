# DEF-04: Adding the same item and option again creates a duplicate cart row

| Field | Details |
|-------|---------|
| Defect ID | DEF-04 |
| Module | Cart |
| Application | BlissBite (localhost:3000) |
| Related test cases | CT_04, CT_06 |
| Reported by | Suman Mulla |
| Date | 18-11-2026 |
| Severity | Minor |
| Priority | Medium |
| Status | Open |

## Description
When an item that is already in the cart is added again with the same portion, the cart shows a separate second row for it instead of merging the two into one row with the quantities and amounts added together. This happens for both the half and the full portion.

## Steps to reproduce
1. Log in as rahul.sharma@test.com and open http://localhost:3000 with an empty cart.
2. Add Veg Fried Rice, quantity 1, half (110) to the cart.
3. Add Veg Fried Rice, quantity 1, half to the cart again.
4. Open the cart.
5. Add Veg Fried Rice, quantity 1, full (200) to the cart, and add it again.
6. Open the cart again.

## Expected result
One Veg Fried Rice half row with quantity 2 and amount 220, and one Veg Fried Rice full row with quantity 2 and amount 400.

## Actual result
- CT_04: two separate Veg Fried Rice half rows, each with quantity 1 and amount 110.
- CT_06: two separate Veg Fried Rice full rows, each with quantity 1 and amount 200.
The total price is still the correct sum of the rows.

## Impact
The cart is cluttered with duplicate rows for the same item and portion. Prices are not affected. Whether the duplicates are carried into the saved order is checked in OR_01 and OR_02.

## Environment
Windows, Brave browser, BlissBite running locally (frontend port 3000, backend port 5000)

## Evidence
- 07_Screenshots/Cart/CT_05_different_option.png (cart before the second half add)
- 07_Screenshots/Cart/CT_04_same_item_twice.png
- 07_Screenshots/Cart/CT_06_full_again.png
