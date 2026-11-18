# DEF-05: "The Cart is Empty!" message is unreadable (dark text on dark background)
 
| Field | Details |
|-------|---------|
| Defect ID | DEF-05 |
| Module | Cart |
| Application | BlissBite (localhost:3000) |
| Related test cases | CT_09, CT_10 |
| Reported by | <name of the person who ran CT_10> |
| Date | 18-11-2026 |
| Severity | Minor |
| Priority | Medium |
| Status | Open |
 
## Description
When the cart is empty, the cart panel shows the message "The Cart is Empty!" in a dark colour on the dark grey background. The message is almost invisible, so the panel looks blank.
 
## Steps to reproduce
1. Log in as rahul.sharma@test.com and open http://localhost:3000.
2. Make sure the cart is empty (the cart badge in the navbar shows 0).
3. Click Cart in the navbar.
## Expected result
The message "The Cart is Empty!" is clearly readable.
 
## Actual result
The panel looks empty. The message is present, but its dark text is almost invisible against the dark background. The cart with items is not affected: its text is white and readable.
 
## Impact
A user may think the cart page is broken or blank. Functionality is not affected, so the impact is cosmetic.
 
## Environment
Windows, Brave browser, BlissBite running locally (frontend port 3000, backend port 5000)
 
## Evidence
- 07_Screenshots/Cart/CT_10_cart_text_before.png
- 07_Screenshots/Cart/CT_09_empty_cart.png
