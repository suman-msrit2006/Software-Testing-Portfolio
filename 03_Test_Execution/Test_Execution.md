# Test Execution Results: BlissBite

| Item | Details |
|------|---------|
| Application | BlissBite (http://localhost:3000, backend http://localhost:5000) |
| Browser | Google Chrome |
| Executed by | Suman J Mulla (1MS23IS130), Nuthana T M (1MS24IS410), Harshitha M V (1MS24IS407) |
| Execution date | 15-11-2026 to 17-11-2026 |
 
**How to fill this sheet:** run each test case in the application, write what actually happened in *Actual Result*, mark *Status* as Pass or Fail, and for every Fail write the defect ID (for example DEF-02) and save a screenshot in `07_Screenshots`.
 
---
 
## 1. Signup

| TC ID | Description | Test Data | Expected Result | Actual Result | Status | Defect ID |
|-------|-------------|-----------|-----------------|---------------|--------|-----------|
| SU_01 | Signup with all valid details | Rahul Sharma, rahul.sharma@test.com, Bengaluru, Test1234 | Account created, user taken to home page | Account created; redirected to the home page | Pass | - |
| SU_02 | Invalid email format | rahul.test.com | Account not created; error shown | Browser validation message "Please include an '@' in the email address" appeared; form was not submitted; no account created (see 07_Screenshots/Signup/SU_02_invalid_email_validation.png) | Pass | - |
| SU_03 | Name with 4 characters | Ravi, su03@test.com | Account not created; error shown | Redirected to the home page as if signup succeeded; no error message shown. Login with su03@test.com / Test1234 then failed with "Enter Valid Credentials", so the account was not created (see 07_Screenshots/Signup/SU_03_name_4_chars.png, SU_03_login_check.png) | Fail | DEF-01 |
| SU_04 | Name with 5 characters | Rahul, su04@test.com | Account created | Account created with a 5-character name; redirected to the home page; login with su04@test.com succeeded (see 07_Screenshots/Signup/SU_04_name_5_chars.png) | Pass | - |
| SU_05 | Password with 4 characters | Ab12, su05@test.com | Account not created; error shown | Redirected to the home page as if signup succeeded; no error message shown. Login with su05@test.com / Ab12 then failed with "Enter Valid Credentials", so the account was not created (see 07_Screenshots/Signup/SU_05_password_4_chars.png, SU_05_login_check.png) | Fail | DEF-01 |
| SU_06 | Password with 5 characters | Ab123, su06@test.com | Account created | Account created with a 5-character password; redirected to the home page; login with su06@test.com succeeded (see 07_Screenshots/Signup/SU_06_password_5_chars.png) | Pass | - |
| SU_07 | Location with 4 characters | Pune, su07@test.com | Account not created; error shown | Redirected to the home page as if signup succeeded; no error message shown. Login with su07@test.com / Test1234 then failed with "Enter Valid Credentials", so the account was not created (see 07_Screenshots/Signup/SU_07_location_4_chars.png, SU_07_login_check.png) | Fail | DEF-01 |
| SU_08 | Location with 5 characters | Delhi, su08@test.com | Account created | Account created with a 5-character location; redirected to the home page; login with su08@test.com succeeded (see 07_Screenshots/Signup/SU_08_location_5_chars.png) | Pass | - |
| SU_09 | Duplicate email | rahul.sharma@test.com (used in SU_01), password Other1234 | Account not created; message that email exists | Redirected to the home page as if signup succeeded; no message that the email already exists. The original password Test1234 still works, so no duplicate account was created (see 07_Screenshots/Signup/SU_09_duplicate_email.png, SU_09_login_check.png) | Fail | DEF-01 |
| SU_10 | All fields empty | All blank | Form not submitted or error shown | Form was submitted with all fields empty; no validation message appeared and the user was redirected to the home page (see 07_Screenshots/Signup/SU_10_all_fields_empty.png) | Fail | DEF-02 |
 
## 2. Login

| TC ID | Description | Test Data | Expected Result | Actual Result | Status | Defect ID |
|-------|-------------|-----------|-----------------|---------------|--------|-----------|
| LG_01 | Valid credentials | rahul.sharma@test.com, Test1234 (account from SU_01) | Login succeeds; home page; navbar shows My Orders and Logout | Login succeeded; redirected to the home page; navbar shows My Orders and Logout (see 07_Screenshots/Login/LG_01_valid_login.png) | Pass | - |
| LG_02 | Correct email, wrong password | rahul.sharma@test.com, Wrong999 | Alert "Enter Valid Credentials" | Alert "Enter Valid Credentials" appeared; user stayed on the login page; navbar still shows Login and Signup (see 07_Screenshots/Login/LG_02_wrong_password.png) | Pass | - |
| LG_03 | Unregistered email | nouser@test.com, Test1234 | Alert "Enter Valid Credentials" | Alert "Enter Valid Credentials" appeared; user stayed on the login page; navbar still shows Login and Signup (see 07_Screenshots/Login/LG_03_unregistered_email.png) | Pass | - |
| LG_04 | Empty fields | Both blank | Login not allowed | Alert "Enter Valid Credentials" appeared; login rejected; user stayed on the login page; navbar still shows Login and Signup. The empty form was sent to the server (no browser "fill out this field" tooltip) (see 07_Screenshots/Login/LG_04_empty_fields.png) | Pass | - |
| LG_05 | 4-character password | rahul.sharma@test.com, Ab12 | Login rejected | Alert "Enter Valid Credentials" appeared; login rejected; user stayed on the login page (see 07_Screenshots/Login/LG_05_password_4_chars.png) | Pass | - |
| LG_06 | Logout after login | Click Logout | Session cleared; login page; navbar shows Login and Signup | Logout cleared the session; user taken to the login page; navbar shows Login and Signup (see 07_Screenshots/Login/LG_06_logged_in_before.png, LG_06_logout.png) | Pass | - |
 
## 3. Menu and search

| TC ID | Description | Test Data | Expected Result | Actual Result | Status | Defect ID |
|-------|-------------|-----------|-----------------|---------------|--------|-----------|
| MN_01 | Home page shows the menu | Open home page | 3 categories with all food items displayed | Home page displayed 3 categories (Pizza, Biryani/Rice, Starter) with all 12 food items, each with name, quantity, option and price. The image for Mix Veg Pizza failed to load (broken image icon), and a broken image icon appears at the top-left under the navbar (see 07_Screenshots/Menu_Search/MN_01_menu_display.png, MN_01_menu_display_2.png, DEF-03_mix_veg_pizza_image.png) | Fail | DEF-03 |
| MN_02 | Search with matching word | paneer | Only items containing "paneer" shown | Typed "paneer" in the search box; only 3 items were shown (Chilli Paneer, Paneer Tikka, Paneer 65) under the Starter category. Other items and empty categories were hidden (see 07_Screenshots/Menu_Search/MN_02_search_paneer.png) | Pass | - |
| MN_03 | Search is not case sensitive | PANEER | Same results as MN_02 | Typed "PANEER" in capitals; the same 3 items as MN_02 were shown (Chilli Paneer, Paneer Tikka, Paneer 65) under the Starter category (see 07_Screenshots/Menu_Search/MN_03_search_uppercase.png) | Pass | - |
| MN_04 | Search with no match | xyz123 | No food items shown | Typed "xyz123"; no food items were shown, category headings were hidden, and the message "No food items found" appeared (see 07_Screenshots/Menu_Search/MN_04_search_no_match.png) | Pass | - |
| MN_05 | Clear the search box | Empty search | All items displayed again | Cleared the search box; all 3 categories (Pizza, Biryani/Rice, Starter) and all 12 food items were displayed again (see 07_Screenshots/Menu_Search/MN_05_search_cleared.png) | Pass | - |
| MN_06 | Price changes with portion size | Switch half and full | Displayed price matches option and quantity | Changed the option and quantity on Paneer 65 (half x1 = ₹150, full x1 = ₹260, full x2 = ₹520). The price changed with each selection and matched quantity x option price (see 07_Screenshots/Menu_Search/MN_06_price_portion.png) | Pass | - |
 
## 4. Cart

| TC ID | Description | Test Data | Expected Result | Actual Result | Status | Defect ID |
|-------|-------------|-----------|-----------------|---------------|--------|-----------|
| CT_01 | Quantity 1 (minimum) | Qty 1, half | 1 row; amount = 1 x half price | Cart showed 1 row: Veg Fried Rice, qty 1, half, amount 110; Total Price 110. (07_Screenshots/Cart/CT_01_qty_1.png) | Pass | - |
| CT_02 | Quantity 6 (maximum) | Qty 6, full | Quantity 6; amount = 6 x full price | Veg Biryani qty 6, full, amount 1560, matching the card price of 1560. Total Price 1670 with the earlier row. (07_Screenshots/Cart/CT_02_qty_6.png) | Pass | - |
| CT_03 | Maximum quantity offered | Open quantity dropdown | Only 1 to 6 offered; 7 not selectable | Quantity dropdown offered 1, 2, 3, 4, 5 and 6 only; no 7 or higher. (07_Screenshots/Cart/CT_03_quantity_options.png) | Pass | - |
| CT_04 | Same item, same option twice | Same item, half, add twice | One row; quantities and amounts added | Adding Veg Fried Rice qty 1, half a second time created a second separate half row (qty 1, 110) instead of one row with qty 2, 220. Total 1980. (07_Screenshots/Cart/CT_04_same_item_twice.png) | Fail | DEF-04 |
| CT_05 | Same item, different option | Half then full | Two separate rows | Veg Fried Rice shown as 2 separate rows: half (qty 1, 110) and full (qty 1, 200). Veg Biryani unchanged. Total 1870. (07_Screenshots/Cart/CT_05_different_option.png) | Pass | - |
| CT_06 | Same option added again after a different option | Half, full, full | Second "full" updates the existing full row; no duplicate row | Adding Veg Fried Rice qty 1, full when a full row already existed created a second separate full row (qty 1, 200) instead of updating it to qty 2, 400. Total 2070. (07_Screenshots/Cart/CT_06_full_again.png) | Fail | DEF-04 |
| CT_07 | Remove an item | Click Remove | Row removed; total updated | Removed one Veg Fried Rice full row; 3 rows remained with numbering updated; total changed from 2070 to 1870. (07_Screenshots/Cart/CT_07_remove_item.png) | Pass | - |
| CT_08 | Total price | 3 items | Total = sum of row amounts | Sum of row amounts 1560 + 110 + 200 = 1870; app Total Price 1870. (07_Screenshots/Cart/CT_08_total_price.png) | Pass | - |
| CT_09 | Empty cart | Nothing in cart | Message "The Cart is Empty!" | Cart opened with the message "The Cart is Empty!" (cart badge 0). The text is very faint; readability is logged under CT_10. (07_Screenshots/Cart/CT_09_empty_cart.png) | Pass | - |
| CT_10 | Cart details readable | Empty cart | All text clearly visible | The message "The Cart is Empty!" is dark text on a dark background and is almost invisible. The cart with items is readable. (07_Screenshots/Cart/CT_10_cart_text_before.png) | Fail | DEF-05 |
| CT_11 | Add to cart without login | Not logged in | Redirected to login page | After logout, the home page showed only Login and Signup, and the login page (Email Address, Password, Submit) was displayed. (07_Screenshots/Cart/CT_11_not_logged_in.png) | Pass | - |

## 5. Order and order history

| TC ID | Description | Test Data | Expected Result | Actual Result | Status | Defect ID |
|-------|-------------|-----------|-----------------|---------------|--------|-----------|
| OR_01 | Place an order | Logged in, items in cart, Check Out | Order saved; cart emptied | Added Veg Biryani (1, half, 150), Veg Fried Rice (1, half, 110) and Chicken Biryani (1, half, 170); cart total 430. After Check Out the cart was emptied and the badge reset to 0. (07_Screenshots/Order_History/OR_01_cart_before_checkout.png, 07_Screenshots/Order_History/OR_01_checkout.png) | Pass | - |
| OR_02 | Order appears in My Orders | After OR_01 | Date, items, quantity, option and price shown | My Orders showed the order dated Wed Nov 18 2026 with Veg Biryani (1, half, 150), Veg Fried Rice (1, half, 110) and Chicken Biryani (1, half, 170). (07_Screenshots/Order_History/OR_02_my_orders.png) | Pass | - |
| OR_03 | Order total matches cart total | Compare cart and My Orders | Sums are equal | Cart total before checkout was 430; the My Orders items add up to 150 + 110 + 170 = 430; the totals are equal. (07_Screenshots/Order_History/OR_03_total_match.png, 07_Screenshots/Order_History/OR_03_cart_total_before.png) | Pass | - |
| OR_04 | Second order on same account | New items, Check Out | New order added; earlier order kept | Second order with 2 items (Prawns Fried Rice 1, half, 120 and Fish Biryani 1, half, 200; total 320) was added at the top of My Orders; the first order with 3 items was still listed. (07_Screenshots/Order_History/OR_04_second_order.png) | Pass | - |
| OR_05 | My Orders with no orders | New account, no orders | Page opens without crashing; empty history | Logged in as su04@test.com; My Orders opened without an error and showed the message "No Order History is Present". (07_Screenshots/Order_History/OR_05_no_orders.png) | Pass | - |
 
 
## Result summary
 
| Module | Total | Passed | Failed |
|--------|-------|--------|--------|
| Signup | 10 | 5 | 5 |
| Login | 6 | 6 | 0 |
| Menu and search | 6 | 5 | 1 |
| Cart | 11 | 8 | 3 |
| Order and history | 5 | 5 | 0 |
| **Total** | **38** | **29** | **9** |
 
# Defects Found

| Defect ID | Module | Summary | Failed Test Cases | Severity | Priority |
|---|---|---|---|---|---|
| DEF-01 | Signup | Invalid inputs (short name, password or location, duplicate email) are silently accepted as successful, without displaying an error message. | SU_03, SU_05, SU_07, SU_09 | **Major** | **High** |
| DEF-02 | Signup | Signup form can be submitted with all fields empty without displaying a validation message. | SU_10 | **Minor** | **Medium** |
| DEF-03 | Menu and Search | Food item image and a page image fail to load on the home page. | MN_01 | **Minor** | **Low** |
| DEF-04 | Cart | Adding the same item with the same portion again creates a duplicate cart row instead of updating the existing entry. | CT_04, CT_06 | **Minor** | **Medium** |
| DEF-05 | Cart | The "The Cart is Empty!" message is unreadable due to dark text on a dark background. | CT_10 | **Minor** | **Low** |
 
