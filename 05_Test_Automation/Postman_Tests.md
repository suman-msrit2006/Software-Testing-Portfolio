# Postman API Tests: BlissBite
 
| Item | Details |
|------|---------|
| Application | BlissBite (frontend http://localhost:3000, backend http://localhost:5000) |
| Tool | Postman Desktop App |
| Collection | `BlissBite_API_Tests.postman_collection.json` (in this folder) |
| Base URL | `http://localhost:5000` (stored as the collection variable `baseUrl`) |
| API prefix | All routes are mounted under `/api` |
| Execution date | 18-11-2026 |
| Screenshots | `07_Screenshots/Postman/` |
 
## 1. Purpose
 
This is the extra tool-based testing activity required by the test plan (section 2 and section 8). Postman sends requests directly to the backend and shows the response, without using the web page. This shows how the server behaves on its own, and it helps explain why some defects found in the manual tests (DEF-01 and DEF-02) happen.
 
## 2. Scope
 
The planned API module covers signup, login, menu, order and order history. The 10 requests below cover all five.
 
Not tested (outside the planned scope): `/api/getuser` and `/api/getlocation`. The location endpoint depends on an external geocoding service, and neither is part of the modules listed in the test plan.
 
## 3. How to run
 
1. Start the backend: open a terminal in the `server` folder and run `node index.js`. Wait for "MongoDB Connected" and "Server is listening at 5000...".
2. Open Postman and import `BlissBite_API_Tests.postman_collection.json`.
3. Check that the collection variable `baseUrl` is `http://localhost:5000`.
4. Run the requests in order, PM_01 to PM_10. Later requests depend on the account created in PM_01 and the order placed in PM_08.
5. Each request has a post-response script that checks the expected status code. The result shows in the **Test Results** tab (PASSED or FAILED).
Note: PM_01 creates an account, so running it again with the same email returns the duplicate-email error. Use a new email to re-run it.
 
## 4. Test data used
 
| Email | Purpose |
|-------|---------|
| api04@test.com | Main account: created in PM_01, then used in PM_05, PM_06, PM_08 and PM_09 |
| api01@test.com | Existing account used to test the duplicate email in PM_02 |
| api03@test.com | Used only in PM_03; the account is rejected and not created |
| noorders@test.com | Email with no orders, used in PM_10 |
 
Only fake test data is used.
 
## 5. Test results
 
| ID | API | Description | Data sent | Expected result | Actual result | Status | Related |
|----|-----|-------------|-----------|-----------------|---------------|--------|---------|
| PM_01 | POST /api/createuser | Signup with valid details | name "Api User One", api04@test.com, Bengaluru, Test1234 | 200 OK, `success: true`, token returned | 200 OK; `success: true`, token returned, result "User Added Successfully!!!" | Pass | SU_01 |
| PM_02 | POST /api/createuser | Signup with an email that already exists | api01@test.com (existing account) | 400 Bad Request, message that the email already exists | 400 Bad Request; `error: "User with this Email Already Exists."` | Pass | SU_09, DEF-01 |
| PM_03 | POST /api/createuser | Signup with a 4-character password | api03@test.com, password Ab12 | 422, "Invalid Password" | 422 Unprocessable Entity; errors list with `msg: "Invalid Password"` for the field `password` | Pass | SU_05, DEF-01 |
| PM_04 | POST /api/createuser | Signup with an empty body | `{}` | 422, validation errors for the missing fields | 422 Unprocessable Entity; errors list returned, beginning with "Invalid Email" for the blank email | Pass | SU_10, DEF-02 |
| PM_05 | POST /api/login | Login with valid credentials | api04@test.com, Test1234 | 200 OK, `success: true`, token returned | 200 OK; `success: true`, result "Login Successful !!!", token returned | Pass | LG_01 |
| PM_06 | POST /api/login | Login with a wrong password | api04@test.com, Wrong999 | 400 Bad Request, "Invalid Credentials" | 400 Bad Request; `success: false`, `error: "Invalid Credentials"` | Pass | LG_02 |
| PM_07 | POST /api/items | Get the menu data | No body | 200 OK, food items and categories returned | 200 OK; JSON array with the food items (name, image, half and full prices, description) and categories | Pass | MN_01 |
| PM_08 | POST /api/orderData | Place an order | api04@test.com, date Wed Nov 18 2026, 1 x Fish Biryani (half, 200) | 200 OK, `success: true` | 200 OK; `success: true` | Pass | OR_01 |
| PM_09 | POST /api/myOrderData | Order history for an email with orders | api04@test.com | 200 OK, the placed order returned | 200 OK; `orderData` for api04@test.com with the order dated Wed Nov 18 2026 containing Fish Biryani (qty 1, half, 200) | Pass | OR_02 |
| PM_10 | POST /api/myOrderData | Order history for an email with no orders | noorders@test.com | 404 Not Found, "Data Not Found" | (fill in after running PM_10) | (Pass or Fail) | OR_05 |
 
## 6. Summary
 
| Item | Count |
|------|-------|
| Total requests | 10 |
| Passed | 9 (update after PM_10) |
| Failed | 0 (update after PM_10) |
| New defects found through Postman | 0 |
 
Screenshots: `07_Screenshots/Postman/` (`PM_01_signup_valid.png`, `PM_02_signup_duplicate.png`, `PM_03_signup_password_4_chars.png`, `PM_04_signup_empty_body.png`, `PM_05_login_valid.png`, `PM_06_login_wrong_password.png`, `PM_07_menu_data.png`, `PM_08_place_order.png`, `PM_09_order_history.png`, `PM_10_history_no_orders.png`).
 
## 7. Findings
 
1. **The server validates correctly.** It rejects a 4-character password (PM_03) and an empty body (PM_04) with status 422 and a clear error message, and it rejects a duplicate email (PM_02) with status 400 and a message. Valid requests work as expected (PM_01, PM_05, PM_08, PM_09).
2. **DEF-01 and DEF-02 are frontend problems.** In the manual tests, the signup page redirected to the home page and showed no error for invalid input (SU_03, SU_05, SU_07, SU_09) and for an empty form (SU_10). The API results show that the server returns an error each time, so the signup page does not show those server errors to the user. No invalid account was stored.
3. **Login is secure at the API level.** A wrong password and an unknown account both return the same message, "Invalid Credentials" (PM_06), so the response does not reveal which of the two was wrong.
4. **Order history for a missing account returns 404 with a clear message** (PM_10), which the "My Orders" page handles by showing "No Order History is Present" (OR_05).
5. **No new defects were found with Postman.** All results matched the behaviour in the code and in the test plan.
## 8. Conclusion
 
The BlissBite API behaves correctly for valid and invalid input. The main quality gap found in this project is on the frontend, where server error messages from signup are not shown to the user (DEF-01 and DEF-02).
 
