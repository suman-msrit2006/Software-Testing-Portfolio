# DEF-03: Mix Veg Pizza image is not loading on the home page

| Field | Details |
|-------|---------|
| Defect ID | DEF-03 |
| Module | Menu Display |
| Application | BlissBite (localhost:3000) |
| Related test cases | MN_01 |
| Reported by | Suman J Mulla |
| Date | 17-11-2026 |
| Severity | Minor |
| Priority | Medium |
| Status | Open |

## Description
The Mix Veg Pizza food item on the home page does not display its actual food image. Instead, a broken image icon is displayed inside the food item card. Other food item images are displayed normally.

## Steps to reproduce
1. Open http://localhost:3000.
2. Log in with valid credentials.
3. Navigate to the home page.
4. Scroll to the Pizza category.
5. Locate the Mix Veg Pizza food item.
6. Observe the image displayed in its food item card.

## Expected result
The Mix Veg Pizza card should display its corresponding food image correctly, just like the other food items displayed in the menu.

## Actual result
The Mix Veg Pizza card displays a broken image icon instead of the actual food image. The food name, quantity selection, portion option, price and Add to Cart button are displayed correctly.

## Impact
Users cannot view the actual image of Mix Veg Pizza before adding it to their cart. This affects the visual presentation of the menu and reduces the consistency of the food ordering experience.

## Environment
Windows, Google Chrome, BlissBite running locally (frontend port 3000, backend port 5000)

- 07_Screenshots/Menu_Search/MN_01_menu_display.png
- 07_Screenshots/Menu_Search/MN_01_menu_display_2.png
