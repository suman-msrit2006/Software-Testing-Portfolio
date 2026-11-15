# Test Execution Results: BlissBite
 
| Item | Details |
|------|---------|
| Application | BlissBite (http://localhost:3000, backend http://localhost:5000) |
| Browser | Google Chrome |
| Executed by | [name] |
| Execution date | [date] |
 
**How to fill this sheet:** run each test case in the application, write what actually happened in *Actual Result*, mark *Status* as Pass or Fail, and for every Fail write the defect ID (for example DEF-02) and save a screenshot in `07_Screenshots`.
 
---
 
## 1. Signup
 
| TC ID | Description | Test Data | Expected Result | Actual Result | Status | Defect ID |
|-------|-------------|-----------|-----------------|---------------|--------|-----------|
| SU_01 | Signup with all valid details | Rahul Sharma, rahul.sharma@test.com, Bengaluru, Test1234 | Account created, user taken to home page | | | |
| SU_02 | Invalid email format | rahul.test.com | Account not created; error shown | | | |
| SU_03 | Name with 4 characters | Ravi | Account not created; error shown | | | |
| SU_04 | Name with 5 characters | Rahul | Account created | | | |
| SU_05 | Password with 4 characters | Ab12 | Account not created; error shown | | | |
| SU_06 | Password with 5 characters | Ab123 | Account created | | | |
| SU_07 | Location with 4 characters | Pune | Account not created; error shown | | | |
| SU_08 | Location with 5 characters | Delhi | Account created | | | |
| SU_09 | Duplicate email | Email used in SU_01 | Account not created; message that email exists | | | |
| SU_10 | All fields empty | All blank | Form not submitted or error shown | | | |
 
## 2. Login
 
| TC ID | Description | Test Data | Expected Result | Actual Result | Status | Defect ID |
|-------|-------------|-----------|-----------------|---------------|--------|-----------|
| LG_01 | Valid credentials | Email and password from SU_01 | Login succeeds; home page; navbar shows My Orders and Logout | | | |
| LG_02 | Correct email, wrong password | Wrong999 | Alert "Enter Valid Credentials" | | | |
| LG_03 | Unregistered email | nouser@test.com | Alert "Enter Valid Credentials" | | | |
| LG_04 | Empty fields | Both blank | Login not allowed | | | |
| LG_05 | 4-character password | Ab12 | Login rejected | | | |
| LG_06 | Logout after login | Click Logout | Session cleared; login page; navbar shows Login and Signup | | | |
 
## 3. Menu and search
 
| TC ID | Description | Test Data | Expected Result | Actual Result | Status | Defect ID |
|-------|-------------|-----------|-----------------|---------------|--------|-----------|
| MN_01 | Home page shows the menu | Open home page | 3 categories with all food items displayed | | | |
| MN_02 | Search with matching word | paneer | Only items containing "paneer" shown | | | |
| MN_03 | Search is not case sensitive | PANEER | Same results as MN_02 | | | |
| MN_04 | Search with no match | xyz123 | No food items shown | | | |
| MN_05 | Clear the search box | Empty search | All items displayed again | | | |
| MN_06 | Price changes with portion size | Switch half and full | Displayed price matches option and quantity | | | |
 
## 4. Cart
 
| TC ID | Description | Test Data | Expected Result | Actual Result | Status | Defect ID |
|-------|-------------|-----------|-----------------|---------------|--------|-----------|
| CT_01 | Quantity 1 (minimum) | Qty 1, half | 1 row; amount = 1 x half price | | | |
| CT_02 | Quantity 6 (maximum) | Qty 6, full | Quantity 6; amount = 6 x full price | | | |
| CT_03 | Maximum quantity offered | Open quantity dropdown | Only 1 to 6 offered; 7 not selectable | | | |
| CT_04 | Same item, same option twice | Same item, half, add twice | One row; quantities and amounts added | | | |
| CT_05 | Same item, different option | Half then full | Two separate rows | | | |
| CT_06 | Same option added again after a different option | Half, full, full | Second "full" updates the existing full row; no duplicate row | | | |
| CT_07 | Remove an item | Click Remove | Row removed; total updated | | | |
| CT_08 | Total price | 3 items | Total = sum of row amounts | | | |
| CT_09 | Empty cart | Nothing in cart | Message "The Cart is Empty!" | | | |
| CT_10 | Cart details readable (DEF-01) | Cart with items | All text and the Check Out label clearly visible | | | |
| CT_11 | Add to cart without login | Not logged in | Redirected to login page | | | |
 
## 5. Order and order history
 
| TC ID | Description | Test Data | Expected Result | Actual Result | Status | Defect ID |
|-------|-------------|-----------|-----------------|---------------|--------|-----------|
| OR_01 | Place an order | Logged in, items in cart, Check Out | Order saved; cart emptied | | | |
| OR_02 | Order appears in My Orders | After OR_01 | Date, items, quantity, option and price shown | | | |
| OR_03 | Order total matches cart total | Compare cart and My Orders | Sums are equal | | | |
| OR_04 | Second order on same account | New items, Check Out | New order added; earlier order kept | | | |
| OR_05 | My Orders with no orders | New account, no orders | Page opens without crashing; empty history | | | |
 
---
 
## Result summary (fill after execution)
 
| Module | Total | Passed | Failed |
|--------|-------|--------|--------|
| Signup | 10 | | |
| Login | 6 | | |
| Menu and search | 6 | | |
| Cart | 11 | | |
| Order and history | 5 | | |
| **Total** | **38** | | |
 
