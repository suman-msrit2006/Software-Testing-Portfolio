# Test Plan: Food Ordering and Delivery Application (BlissBite)
 
| Item | Details |
|------|---------|
| Project | Software Testing Portfolio |
| Application under test | BlissBite (https://github.com/vrun545/food-delivery-app) |
| Prepared by | Suman J Mulla (1MS23IS130), Nuthana T M (1MS24IS410), Harshitha M V (1MS24IS407) |
| College | M. S. Ramaiah Institute of Technology (MSRIT), Information Science and Engineering, 7th Semester, B Section |
| Faculty | Pushpalatha |
| Version | 1.0 |
| Date | 15-11-2026 |
 
---
 
## 1. Introduction
This document describes how we will test BlissBite, an open-source MERN stack food ordering application. Users can sign up, log in, browse the menu by category, search for food items, choose a portion size and quantity, add items to a cart, place orders and view their order history. The plan covers what will be tested, how, by whom and with which tools.
 
## 2. Objectives
- Verify that the main functions of the application work as expected.
- Check input validation and boundary conditions in signup, login and the cart.
- Verify the order flow from cart to order history.
- Find and document defects with clear evidence.
- Carry out one tool-based testing activity (API testing with Postman).
- 
## 3. Application Under Test
| Item | Details |
|------|---------|
| Name | BlissBite |
| Source | https://github.com/vrun545/food-delivery-app |
| Type | Web application (client and server) |
| Technology | React (frontend), Node.js and Express (backend), MongoDB Atlas (database) |
| How it is run | Locally. Frontend at http://localhost:3000, backend at http://localhost:5000 |
| License | MIT |
 
The application was written by its original author. We test it as the system under test. No changes were made to the application.
 
## 4. Scope
 
### 4.1 In scope
| Module | Functions tested |
|--------|------------------|
| Signup | Registration with name, email, location and password; field validation; duplicate email |
| Login and logout | Login with valid and invalid credentials; logout |
| Menu and search | Menu display by category; search by food name; portion price display |
| Cart | Add item (half or full portion, quantity 1 to 6); update; remove; total price; empty cart |
| Order placement | Check out from the cart |
| Order history | My Orders page with date, items, quantity, option and price |
| API | Signup, login, menu, order and order history endpoints (Postman) |
 
### 4.2 Out of scope
- Online payment (the application has no payment gateway)
- Admin panel and restaurant management (not available)
- Delivery tracking (not available)
- Performance, load and security testing
- Mobile app and cross-browser testing (Google Chrome only)
## 5. Types of Testing
- Functional testing
- Input validation and boundary testing
- Usability and display checks (for example, readability of the cart)
- API testing using Postman
- Retesting of fixed defects
## 6. Test Design Techniques
| Technique | Where it is applied |
|-----------|---------------------|
| Equivalence Partitioning | Valid and invalid email, name, location, password; search words |
| Boundary Value Analysis | Minimum field length of 5 characters; quantity range of 1 to 6 |
| Decision Table | Login outcome based on whether the email is registered and the password is correct |
| State Transition | Order flow: logged out, logged in, cart with items, order placed, logged out |
 
The detailed test cases are in `02_Test_Case_Design/Test_Cases.md`.
 
## 7. Test Environment
| Item | Details |
|------|---------|
| Operating system | Windows |
| Browser | Google Chrome (latest) |
| Runtime | Node.js |
| Database | MongoDB Atlas (free tier) |
| Tools | Postman, Visual Studio Code / Kiro, GitHub |
| Test data | Test accounts created during testing (for example, rahul.sharma@test.com); the 12 sample food items loaded from the project's data files |
 
## 8. Test Deliverables
| Deliverable | Location |
|-------------|----------|
| Test plan | 01_Test_Plan |
| Test cases | 02_Test_Case_Design |
| Test execution results | 03_Test_Execution |
| Defect reports | 04_Defect_Reports |
| Postman API tests | 05_Test_Automation |
| Test summary report | 06_Test_Reports |
| Screenshots | 07_Screenshots |
| Conclusion | Conclusion.md |
 
## 9. Roles and Responsibilities
| Member | USN | Responsibility |
|--------|-----|----------------|
| Suman J Mulla | 1MS23IS130 | Test plan, signup and login test cases, README |
| Nuthana T M | 1MS24IS410 | Menu, search and cart test cases, defect reports |
| Harshitha M V | 1MS24IS407 | Order and history test cases, Postman API testing |
 
All members take part in execution, and each member commits their own work to the repository.
 
## 10. Schedule
| Activity | Planned date |
|----------|--------------|
| Environment setup and application exploration | 14-11-2026 |
| Test plan | 15-11-2026 |
| Test case design | 15-11-2026 |
| Test execution | 17-11-2026 |
| Defect reporting | 17-11-2026 |
| Postman API testing | 17-11-2026 |
| Test summary report and conclusion | 17-11-2026 |
| Demonstration to faculty | 18-11-2026 |
 
## 11. Entry and Exit Criteria
**Entry criteria**
- The backend, frontend and database are running without errors.
- Sample food items are loaded in the database.
- Test cases are written and reviewed by the team.
**Exit criteria**
- All planned test cases are executed and their results recorded.
- All defects found are documented with evidence.
- The test summary report is prepared and uploaded to the repository.
## 12. Defect Severity and Priority
| Severity | Meaning |
|----------|---------|
| Critical | Application crashes or a core function (login, order) cannot be used |
| Major | An important function fails, or the user cannot understand what is happening |
| Minor | A small functional or display problem with an easy workaround |
| Trivial | Cosmetic issue |
 
| Priority | Meaning |
|----------|---------|
| High | Fix first |
| Medium | Fix after high priority items |
| Low | Fix if time allows |
 
Defect status values: Open, Fixed, Verified, Closed.
 
## 13. Risks and Mitigation
| Risk | Mitigation |
|------|-----------|
| The database or internet connection is unavailable | Retry later; keep the connection string and credentials ready |
| The application has limited features | Cover the available modules thoroughly and list unavailable features as out of scope |
| Limited time before the demo | Test the core modules (signup, login, cart, order) first |
| Test data changes between runs | Use separate test accounts and note the data used in each test |
| Changing the application code could affect results | Record every change in a defect report and retest |
 
## 14. Assumptions
- The application behaves according to its code and visible validation rules, which serve as the expected results.
- Only fake test data is used. No real personal or payment details are entered.
 
