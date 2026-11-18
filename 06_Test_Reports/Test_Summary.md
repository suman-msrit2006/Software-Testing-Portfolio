# Test Summary: BlissBite Food Ordering and Delivery Application
 
## 1. Overview
 
| Item | Details |
|------|---------|
| Application under test | BlissBite (https://github.com/vrun545/food-delivery-app) |
| Frontend / backend | http://localhost:3000 / http://localhost:5000 |
| Testing types | Manual functional testing, API testing (Postman) |
| Browser | Google Chrome |
| Tools | Browser, MongoDB Atlas, Postman Desktop App, GitHub |
| Execution period | 15-11-2026 to 18-11-2026 |
| Tested by | Suman J Mulla (1MS23IS130), Nuthana T M (1MS24IS410), Harshitha M V (1MS24IS407) |
 
## 2. Manual test results
 
| Module | Total | Passed | Failed | Failed cases |
|--------|-------|--------|--------|--------------|
| Signup | 10 | 5 | 5 | SU_03, SU_05, SU_07, SU_09, SU_10 |
| Login | 6 | 6 | 0 | none |
| Menu and search | 6 | 5 | 1 | MN_01 |
| Cart | 11 | 8 | 3 | CT_04, CT_06, CT_10 |
| Order and history | 5 | 5 | 0 | none |
| **Total** | **38** | **29** | **9** | |
 
Pass rate: 29 / 38 = 76.3%. Fail rate: 9 / 38 = 23.7%.
 
## 3. API test results (Postman)
 
| Item | Details |
|------|---------|
| Requests executed | 10 (PM_01 to PM_10) |
| Passed | 10 |
| Failed | 0 |
| New defects found | 0 |
| Coverage | Signup, login, menu, order, order history |
| Details | `05_Test_Automation/Postman_Tests.md` |
| Collection | `05_Test_Automation/BlissBite_API_Tests.postman_collection.json` |
 
## 4. Defects found
 
| Defect ID | Module | Summary | Failed test cases | Severity | Priority |
|-----------|--------|---------|-------------------|----------|----------|
| DEF-01 | Signup | Invalid input (short name, password or location, duplicate email) shows no error. The page redirects to the home page as if signup worked, but no account is created. | SU_03, SU_05, SU_07, SU_09 | Major | High |
| DEF-02 | Signup | The signup form can be submitted with all fields empty, with no validation message. | SU_10 | Minor | Medium |
| DEF-03 | Menu and search | A food item image (Mix Veg Pizza) and a page image fail to load on the home page. | MN_01 | Minor | Low |
| DEF-04 | Cart | Adding the same item with the same portion again creates a duplicate cart row instead of updating the existing one. | CT_04, CT_06 | Minor | Medium |
| DEF-05 | Cart | The "The Cart is Empty!" message is dark text on a dark background and is almost unreadable. | CT_10 | Minor | Low |
 
Defect distribution:
 
| Severity | Count | | Priority | Count |
|----------|-------|---|----------|-------|
| Major | 1 | | High | 1 |
| Minor | 4 | | Medium | 2 |
| | | | Low | 2 |
 
Each defect has its own report in the defects folder, with screenshots in `07_Screenshots`.
 
## 5. Observations
 
1. **Signup validation is the weakest area.** 5 of the 10 signup cases failed (DEF-01 and DEF-02).
2. **DEF-01 and DEF-02 are frontend problems.** Postman shows the server rejects invalid input with status 400 or 422 and a clear message (PM_02, PM_03, PM_04), but the signup page does not show these errors to the user. Login checks in the manual tests confirmed that no account was created for the invalid inputs.
3. **Login, order placing and order history work correctly** in all manual and API tests. A wrong password returns "Invalid Credentials" without revealing whether the email or password was wrong.
4. **Cart has a logic defect and a readability defect.** Duplicate rows appear for the same item and portion (DEF-04), and the empty-cart message is unreadable (DEF-05). Totals were still calculated correctly.
5. **The menu works correctly** (search, case-insensitive search, no-match message, price by portion). The only failure is an image that does not load (DEF-03).
## 6. Conclusion
 
38 manual test cases and 10 API requests were executed. 29 manual cases passed and 9 failed, and all 9 failures map to 5 defects (DEF-01 to DEF-05). All 10 API requests passed. The core flows (login, ordering, order history, menu search) work correctly. Signup error handling and the cart need to be fixed before release, with DEF-01 as the highest priority.
 
