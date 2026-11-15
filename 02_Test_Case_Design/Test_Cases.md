# Test Case Design: Food Ordering and Delivery Application (BlissBite)
 
**Application under test:** BlissBite, an open-source MERN food ordering app (github.com/vrun545/food-delivery-app), run locally at http://localhost:3000
**Prepared by:** Suman J Mulla (1MS23IS130), Nuthana T M (1MS24IS410), Harshitha M V (1MS24IS407)
**Techniques used:** Equivalence Partitioning (EP), Boundary Value Analysis (BVA), Decision Table, State Transition
 
> Expected results are based on the application's validation rules: email, name, location and password each need at least 5 characters, email must be a valid format, and the quantity dropdown offers 1 to 6. Actual results and Pass/Fail are recorded in `03_Test_Execution`.
 
---
 
## 1. Signup module
 
| TC ID | Technique | Description | Test Data | Expected Result |
|-------|-----------|-------------|-----------|-----------------|
| SU_01 | EP (valid) | Signup with all valid details | Name: Rahul Sharma, Email: rahul.sharma@test.com, Location: Bengaluru, Password: Test1234 | Account is created and the user is taken to the home page |
| SU_02 | EP (invalid) | Signup with invalid email format | Email: rahul.test.com (other fields valid) | Account is not created; an error is shown to the user |
| SU_03 | BVA (below min) | Name with 4 characters | Name: Ravi | Account is not created; an error is shown |
| SU_04 | BVA (at min) | Name with exactly 5 characters | Name: Rahul | Account is created |
| SU_05 | BVA (below min) | Password with 4 characters | Password: Ab12 | Account is not created; an error is shown |
| SU_06 | BVA (at min) | Password with exactly 5 characters | Password: Ab123 | Account is created |
| SU_07 | BVA (below min) | Location with 4 characters | Location: Pune | Account is not created; an error is shown |
| SU_08 | BVA (at min) | Location with exactly 5 characters | Location: Delhi | Account is created |
| SU_09 | EP (invalid) | Signup with an already registered email | Email used in SU_01 | Account is not created; message that the email already exists |
| SU_10 | EP (invalid) | Signup with all fields empty | All blank | Form is not submitted or an error is shown; no account created |
 
## 2. Login module
 
| TC ID | Technique | Description | Test Data | Expected Result |
|-------|-----------|-------------|-----------|-----------------|
| LG_01 | EP (valid) | Login with correct credentials | Email and password from SU_01 | Login succeeds, user is taken to the home page, navbar shows My Orders and Logout |
| LG_02 | EP (invalid) | Login with correct email, wrong password | Email from SU_01, Password: Wrong999 | Alert "Enter Valid Credentials"; user stays on the login page |
| LG_03 | EP (invalid) | Login with unregistered email | nouser@test.com, any password | Alert "Enter Valid Credentials" |
| LG_04 | EP (invalid) | Login with empty fields | Both blank | Login is not allowed |
| LG_05 | BVA (below min) | Login with a 4-character password | Email from SU_01, Password: Ab12 | Login is rejected |
| LG_06 | State transition | Logout after login | Click Logout | Session is cleared, user goes to the login page, navbar shows Login and Signup |
 
### Decision table: Login
 
| Rule | Email registered? | Password correct? | Expected outcome |
|------|-------------------|-------------------|------------------|
| R1 | Yes | Yes | Login successful |
| R2 | Yes | No | Error "Enter Valid Credentials" |
| R3 | No | Yes (not applicable) | Error "Enter Valid Credentials" |
| R4 | No | No | Error "Enter Valid Credentials" |
 
Test cases covering the rules: R1 = LG_01, R2 = LG_02, R3 and R4 = LG_03.
 
## 3. Menu and search module
 
| TC ID | Technique | Description | Test Data | Expected Result |
|-------|-----------|-------------|-----------|-----------------|
| MN_01 | EP | Home page shows the menu | Open home page | 3 categories (Biryani/Rice, Starter, Pizza) with all food items are displayed |
| MN_02 | EP (valid) | Search with a matching word | paneer | Only items whose name contains "paneer" are shown |
| MN_03 | EP (valid) | Search is not case sensitive | PANEER | Same results as MN_02 |
| MN_04 | EP (invalid) | Search with no matching item | xyz123 | No food items are shown |
| MN_05 | EP | Clear the search box | Empty search | All items are displayed again |
| MN_06 | EP | Price changes with portion size | Switch an item between half and full | Displayed price matches the selected option and quantity |
 
## 4. Cart module
 
| TC ID | Technique | Description | Test Data | Expected Result |
|-------|-----------|-------------|-----------|-----------------|
| CT_01 | BVA (min) | Add an item with quantity 1 | Qty: 1, Option: half | Cart shows 1 row with amount = 1 x half price |
| CT_02 | BVA (max) | Add an item with quantity 6 | Qty: 6, Option: full | Cart shows quantity 6 with amount = 6 x full price |
| CT_03 | BVA (above max) | Check the maximum quantity available | Open the quantity dropdown | Only 1 to 6 are offered; 7 is not selectable |
| CT_04 | EP | Add the same item and same option twice | Same item, half, add twice | One row with quantities and amounts added together |
| CT_05 | EP | Add the same item with a different option | Same item, half then full | Two separate rows, one for each option |
| CT_06 | EP | Add the same item with a second option, then add that option again | Item: half, full, full | The second "full" updates the existing full row (no duplicate row) |
| CT_07 | EP | Remove an item | Click Remove on one row | Row is removed and the total is updated |
| CT_08 | EP | Total price calculation | 3 items in the cart | Total = sum of all row amounts |
| CT_09 | EP | Open the cart with nothing in it | Empty cart | Message "The Cart is Empty!" is displayed |
| CT_10 | EP | Cart details are readable (DEF-01) | Cart with items | Item name, quantity, option, amount, total and Check Out text are clearly visible |
| CT_11 | EP | Add to cart without logging in | Not logged in, select quantity or option | User is redirected to the login page |
 
## 5. Order and order history module
 
| TC ID | Technique | Description | Test Data | Expected Result |
|-------|-----------|-------------|-----------|-----------------|
| OR_01 | State transition | Place an order from the cart | Logged in user, items in the cart, click Check Out | Order is saved and the cart is emptied |
| OR_02 | EP | Order appears in My Orders | After OR_01 | My Orders shows today's date with each item, quantity, option and price |
| OR_03 | EP | Order total matches the cart total | Compare cart total with My Orders amounts | Sum of the items in My Orders equals the cart total |
| OR_04 | State transition | Place a second order on the same account | New items, Check Out | New order is added to the history without removing the earlier order |
| OR_05 | EP | Open My Orders with no previous orders | New account with no orders | Page opens without crashing and shows an empty history |
 
### State transition: Order flow
 
| Current state | Event | Next state |
|---------------|-------|-----------|
| Logged out | Login with valid credentials | Logged in, cart empty |
| Logged in, cart empty | Add item | Cart has items |
| Cart has items | Remove last item | Cart empty |
| Cart has items | Check Out | Order placed, cart empty, order in history |
| Logged in | Logout | Logged out |
 
Test cases covering the transitions: LG_01, LG_06, CT_01, CT_07, OR_01, OR_02, OR_04.
 
---
 
## Summary
 
| Module | Test cases |
|--------|-----------|
| Signup | 10 |
| Login | 6 |
| Menu and search | 6 |
| Cart | 11 |
| Order and history | 5 |
| **Total** | **38** |
 
