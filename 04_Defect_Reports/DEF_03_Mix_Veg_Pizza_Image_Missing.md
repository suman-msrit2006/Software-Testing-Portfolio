# DEF-03: Mix Veg Pizza image fails to load on the home page
 
| Field | Details |
|-------|---------|
| Defect ID | DEF-03 |
| Module | Menu and search |
| Application | BlissBite (localhost:3000) |
| Related test cases | MN_01 |
| Reported by | Suman J Mulla |
| Date | 17-11-2026 |
| Severity | Minor |
| Priority | Medium |
| Status | Open |
 
## Description
 
On the home page, the food card for **Mix Veg Pizza** (Pizza category) does not show its picture. A broken-image icon with "..." is displayed in place of the image. All other food items load their images correctly. A small broken-image icon is also visible at the top-left of the page, just below the navbar.
 
## Steps to Reproduce
 
1. Start the backend (`npm start` in the server folder) and the frontend (`npm start` in Client\food-app).
2. Log in with rahul.sharma@test.com / Test1234.
3. Open http://localhost:3000 and refresh the page.
4. Look at the Pizza category at the top of the page.
## Expected Result
 
Every food item, including Mix Veg Pizza, shows its image on the card.
 
## Actual Result
 
The Mix Veg Pizza card shows a broken-image icon instead of a picture. The other 11 items display their images. A broken-image icon also appears at the top-left under the navbar.
 
## Impact
 
The item is still listed with its name, option, quantity and price, and it can be added to the cart, so ordering is not blocked. The missing image makes the menu look unfinished and may reduce the chance of the item being ordered.
 
## Possible Cause
 
The image URL stored for this item in the database may be invalid, expired or blocked. This needs to be confirmed by the developer.
 
## Evidence
 
- `07_Screenshots/Menu_Search/DEF-03_mix_veg_pizza_image.png` (close-up of the Mix Veg Pizza card)
- `07_Screenshots/Menu_Search/MN_01_menu_display.png` (top of the home page)
- `07_Screenshots/Menu_Search/MN_01_menu_display_2.png` (rest of the home page)
 
