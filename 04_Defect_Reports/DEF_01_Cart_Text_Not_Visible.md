# DEF-01: No error message when signup fails; user is redirected as if successful

| Field | Details |
|-------|---------|
| Defect ID | DEF-01 |
| Module | Signup |
| Application | BlissBite (localhost:3000) |
| Related test cases | SU_03, SU_05, SU_07 |
| Reported by | Suman J Mulla |
| Date | 15-11-2026 |
| Severity | Major |
| Priority | High |
| Status | Open |

## Description
When signup is rejected by the server (for example, because the name, password or location is shorter than 5 characters), the application still redirects the user to the home page and shows no error message. The user believes the account was created, but it was not.

## Steps to reproduce

**Case 1 (SU_03): name too short**
1. Open http://localhost:3000/signup.
2. Enter Name: Ravi, Email: su03@test.com, Location: Bengaluru, Password: Test1234.
3. Click Submit.
4. Open http://localhost:3000/login and log in with su03@test.com and Test1234.

**Case 2 (SU_05): password too short**
1. Open http://localhost:3000/signup.
2. Enter Name: Rahul Sharma, Email: su05@test.com, Location: Bengaluru, Password: Ab12.
3. Click Submit.
4. Open http://localhost:3000/login and log in with su05@test.com and Ab12.

**Case 3 (SU_07): location too short**
1. Open http://localhost:3000/signup.
2. Enter Name: Rahul Sharma, Email: su07@test.com, Location: Pune, Password: Test1234.
3. Click Submit.
4. Open http://localhost:3000/login and log in with su07@test.com and Test1234.

## Expected result
Signup fails with a clear error message (for example, "Name must be at least 5 characters"), and the user stays on the signup page. No account is created.

## Actual result
In all three cases the user is taken to the home page and no message is shown. The login in step 4 then fails with "Enter Valid Credentials", which shows that no account was created.

## Impact
Users who enter invalid data are misled about their account status and cannot tell why they cannot log in later. The problem affects every field the server validates (name, password and location), so it comes from how the signup page handles any rejected form.

## Environment
Windows, Google Chrome, BlissBite running locally (frontend port 3000, backend port 5000)

## Evidence
- 07_Screenshots/SU_03_name_4_chars.png
- 07_Screenshots/SU_03_login_check.png
- 07_Screenshots/SU_05_password_4_chars.png
- 07_Screenshots/SU_05_login_check.png
- 07_Screenshots/SU_07_location_4_chars.png
- 07_Screenshots/SU_07_login_check.png
