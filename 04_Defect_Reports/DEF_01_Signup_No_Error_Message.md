# DEF-01: No error message when signup fails; user is redirected as if successful

| Field | Details |
|-------|---------|
| Defect ID | DEF-01 |
| Module | Signup |
| Application | BlissBite (localhost:3000) |
| Related test cases | SU_03, SU_05, SU_07, SU_09 |
| Reported by | Suman J Mulla |
| Date | 15-11-2026 |
| Severity | Major |
| Priority | High |
| Status | Open |

## Description
When signup is rejected by the server (for example, because the name, password or location is shorter than 5 characters, or because the email is already registered), the application still redirects the user to the home page and shows no error message. The user believes the account was created, but it was not.

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

**Case 4 (SU_09): email already registered**
1. Make sure rahul.sharma@test.com is already registered with password Test1234 (SU_01).
2. Open http://localhost:3000/signup.
3. Enter Name: Rahul Sharma, Email: rahul.sharma@test.com, Location: Bengaluru, Password: Other1234.
4. Click Submit.
5. Open http://localhost:3000/login and log in with rahul.sharma@test.com and Test1234.

## Expected result
Signup fails with a clear error message (for example, "Name must be at least 5 characters" or "A user with this email already exists"), and the user stays on the signup page. No account is created or changed.

## Actual result
In all four cases the user is taken to the home page and no message is shown. In cases 1 to 3 the login in the last step fails with "Enter Valid Credentials", which shows that no account was created. In case 4 the original password still works, so no duplicate account was created, but the user is not told that the email is already registered.

## Impact
Users who enter invalid data, or an email that is already registered, are misled about their account status and cannot tell why they cannot log in later. The problem affects every rejection the server makes (name, password, location and duplicate email), so it comes from how the signup page handles any rejected form.

## Environment
Windows, Google Chrome, BlissBite running locally (frontend port 3000, backend port 5000)

- 07_Screenshots/Signup/SU_03_name_4_chars.png
- 07_Screenshots/Signup/SU_03_login_check.png
- 07_Screenshots/Signup/SU_05_password_4_chars.png
- 07_Screenshots/Signup/SU_05_login_check.png
- 07_Screenshots/Signup/SU_07_location_4_chars.png
- 07_Screenshots/Signup/SU_07_login_check.png
- 07_Screenshots/Signup/SU_09_duplicate_email.png
- 07_Screenshots/Signup/SU_09_login_check.png
