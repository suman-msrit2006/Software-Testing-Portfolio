# DEF-01: No error message when signup fails; user is redirected as if successful

| Field | Details |
|-------|---------|
| Defect ID | DEF-01 |
| Module | Signup |
| Application | BlissBite (localhost:3000) |
| Related test cases | SU_03 (add SU_05, SU_07, SU_09 and others after you run them) |
| Reported by | [your name] |
| Date | 15-11-2026 |
| Severity | Major |
| Priority | High |
| Status | Open |

## Description
When signup is rejected by the server (for example, a name shorter than 5 characters), the application still redirects the user to the home page and shows no error message. The user believes the account was created, but it was not.

## Steps to reproduce
1. Open http://localhost:3000/signup.
2. Enter Name: Ravi, Email: su03@test.com, Location: Bengaluru, Password: Test1234.
3. Click Submit.
4. Try to log in at http://localhost:3000/login with su03@test.com and Test1234.

## Expected result
Signup fails with a clear error message (for example, "Name must be at least 5 characters") and the user stays on the signup page. No account is created.

## Actual result
The user is taken to the home page with no message. The login in step 4 fails with "Enter Valid Credentials", showing that no account exists.

## Impact
Users who enter invalid data are misled about their account status and cannot tell why they cannot log in later.

## Environment
Windows, Google Chrome, BlissBite running locally (frontend port 3000, backend port 5000)

## Evidence
- 07_Screenshots/SU_03_name_4_chars.png
- 07_Screenshots/SU_03_login_check.png
