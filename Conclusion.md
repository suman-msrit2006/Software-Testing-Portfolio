# Conclusion: BlissBite Software Testing Portfolio
 
## 1. What was done
 
This portfolio tests the BlissBite Food Ordering and Delivery application (https://github.com/vrun545/food-delivery-app). We did not build the application. We planned the testing, executed it, and documented every step in this repository.
 
| Activity | Result |
|----------|--------|
| Test plan | Scope, modules, approach and environment defined |
| Manual testing | 38 test cases across 5 modules (Signup, Login, Menu and search, Cart, Order and history) |
| API testing | 10 Postman requests covering signup, login, menu, order and order history |
| Defect reporting | 5 defects (DEF-01 to DEF-05), each with its own report and screenshots |
| Test summary | Module-wise results, defect summary and observations |
 
## 2. Results
 
| Type | Total | Passed | Failed |
|------|-------|--------|--------|
| Manual test cases | 38 | 29 | 9 |
| Postman API requests | 10 | 10 | 0 |
 
The 9 failed manual cases map to 5 defects: 1 Major and 4 Minor.
 
| Defect | Module | Severity |
|--------|--------|----------|
| DEF-01 | Signup: invalid input shows no error | Major |
| DEF-02 | Signup: empty form can be submitted | Minor |
| DEF-03 | Menu: image fails to load | Minor |
| DEF-04 | Cart: duplicate rows for the same item and portion | Minor |
| DEF-05 | Cart: empty-cart message unreadable | Minor |
 
## 3. Key findings
 
1. **Core flows work.** Login, menu search, order placing and order history passed in all manual and API tests.
2. **Signup error handling is the main weakness.** The server rejects invalid input correctly (Postman PM_02 to PM_04), but the signup page does not show the errors to the user (DEF-01 and DEF-02). Testing at both the UI and API level showed the problem is in the frontend, not the backend.
3. **The cart needs fixes.** It creates duplicate rows instead of updating an existing one (DEF-04) and the empty-cart message cannot be read (DEF-05).
4. **No security or data problems appeared in the API tests.** A wrong password and an unknown account return the same message, and invalid accounts were not stored.
## 4. Recommendations
 
1. Show the server's error messages on the signup page and add client-side validation for name, password and location length, and for empty fields (DEF-01, DEF-02).
2. Merge cart entries with the same item and portion into one row (DEF-04).
3. Change the text colour of the empty-cart message (DEF-05).
4. Fix or replace the broken image links (DEF-03).
5. Re-run the failed test cases (SU_03, SU_05, SU_07, SU_09, SU_10, MN_01, CT_04, CT_06, CT_10) after the fixes.
## 5. Limitations
 
- Testing covered one browser and a local setup only.
- Performance, security and load testing were outside the scope.
- `/api/getuser` and `/api/getlocation` were not tested through Postman.
## 6. What we learned
 
- Writing test cases with clear expected results makes failures easy to spot and report.
- Combining manual testing with API testing helps find where a defect comes from.
- Good evidence (screenshots, exact test data, dates) makes a defect report useful to a developer.
## 7. Repository guide
 
| Folder | Contents |
|--------|----------|
| Test plan | Test plan |
| Test cases and execution | Test case execution sheet with results |
| Defect reports | DEF-01 to DEF-05 |
| 05_Test_Automation | Postman_Tests.md, collection JSON, environment JSON |
| 06 (Test summary) | Test_Summary.md |
| 07_Screenshots | Evidence for manual and Postman tests |
 
