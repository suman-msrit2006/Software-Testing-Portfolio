# DEF-02: Signup form can be submitted with all fields empty

| Field | Details |
|-------|---------|
| Defect ID | DEF-02 |
| Module | Signup |
| Application | BlissBite (localhost:3000) |
| Related test cases | SU_10 |
| Related defects | DEF-01 (no error message when signup is rejected) |
| Reported by | Suman J Mulla |
| Date | 15-11-2026 |
| Severity | Minor |
| Priority | Medium |
| Status | Open |

## Description
The signup form does not require any field. When all four fields (name, email, location and password) are left empty, the form is submitted, no validation message is shown, and the user is redirected to the home page.

## Steps to reproduce
1. Open http://localhost:3000/signup.
2. Leave Name, Email, Location and Password empty.
3. Click Submit.

## Expected result
The form is not submitted. The browser or the application shows a message asking the user to fill in the empty fields, and the user stays on the signup page.

## Actual result
The form is submitted without any message and the user is taken to the home page.

## Impact
Users can submit an empty form and are misled into thinking signup worked. No account data is stored (the server's own 5-character rule rejects it), so the problem is limited to missing client-side validation and poor feedback. Compare this with SU_02, where the browser did block an email without an "@".

## Environment
Windows, Google Chrome, BlissBite running locally (frontend port 3000, backend port 5000)

## Evidence
- 07_Screenshots/Signup/SU_10_all_fields_empty.png
