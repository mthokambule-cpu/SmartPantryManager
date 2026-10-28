# Smart Pantry Manager

A Java Android app that reduces food waste by tracking the ingredients you already own and
suggesting **only** recipes you can cook right now - no shopping trip required.

## Features
- Add / edit / delete pantry items (name, quantity, unit, optional expiry date) with validation
- 18 pre-seeded recipes (loaded on first run)
- **Strict matching**: a recipe is suggested only if *every* ingredient is in the pantry in at least the
  required quantity. Handles singular/plural names ("tomato" = "tomatoes") and unit conversion (kg/g, l/ml, tbsp...)
- Recipe detail screen, friendly empty state, settings screen (expiry highlighting toggle)
- No Google Maps, GPS or location features

## Database choice: SQLite (SQLiteOpenHelper)
Runs fully on-device, needs no server or internet, persists data between launches, and is the approach
covered in the module's persistent-data chapter. Tables: `pantry`, `recipes`, `recipe_ingredients`.

## Setup / run
1. Install Android Studio (Hedgehog or newer).
2. `File > Open` and select the `SmartPantryManager` folder; let Gradle sync.
3. Choose an emulator (API 24+) or a physical device and press **Run**.

## Project structure
- `MatchEngine` - strict-matching logic  |  `UnitUtils` - name/unit normalisation
- `DatabaseHelper` - SQLite CRUD + recipe seeding
- `MainActivity`, `AddEditItemActivity`, `SuggestedRecipesActivity`, `RecipeDetailActivity`, `SettingsActivity`
- `PantryAdapter`, `RecipeAdapter` - RecyclerView adapters
