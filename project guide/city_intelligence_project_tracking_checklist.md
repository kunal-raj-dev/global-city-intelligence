# City Intelligence — Project Tracking Checklist

> **Use this file only for tracking progress.**
>
> The main roadmap explains *what to learn and why*.
> This checklist answers only: **“What have I completed?”**

---

# 0. Project Setup & Rules

- [ ] I understand the full product I am building.
- [ ] I understand the data flow:
  `SEARCH → GEOCODING → LOCATION → WEATHER / WORLD BANK / USGS → NORMALIZE → STATE → DERIVE → RENDER`
- [ ] I am using HTML, CSS, and Vanilla JavaScript only.
- [ ] I am not using React, TypeScript, Node, backend, database, auth, or unnecessary libraries.
- [ ] I will try to solve problems before asking for the solution.
- [ ] I will inspect API responses before writing code around them.
- [ ] I will not copy code I cannot explain.
- [ ] I will test each phase before moving forward.

---

# Phase 0 — Understand Product & APIs

## Product Understanding

- [ ] I can explain what the dashboard does in my own words.
- [ ] I can explain the complete user journey.
- [ ] I drew a rough wireframe of the main dashboard.
- [ ] I kept the wireframe focused on structure, not visual perfection.
- [ ] I sketched the initial/empty state.
- [ ] I sketched the search-results state.
- [ ] I sketched the selected-city loading state.
- [ ] I sketched the dashboard success state.
- [ ] I sketched an error state.
- [ ] I sketched a no-results/no-earthquakes state.
- [ ] I know what happens when a user searches for a city.
- [ ] I know how a city becomes the selected location.
- [ ] I know how the selected location drives the other API requests.
- [ ] I understand which data belongs to weather, country intelligence, and earthquakes.

## API Inspection

- [ ] I manually inspected the Open-Meteo Geocoding API.
- [ ] I manually inspected the Open-Meteo Forecast API.
- [ ] I manually inspected the World Bank API.
- [ ] I manually inspected the USGS Earthquake API.
- [ ] I recorded the important request parameters for each API.
- [ ] I recorded the useful response fields for each API.
- [ ] I identified arrays in each response.
- [ ] I identified nested objects in each response.
- [ ] I identified fields that can be `null` or missing.
- [ ] I understand the units returned by each API.
- [ ] I understand how coordinates are represented.
- [ ] I understand the important IDs/codes used by the APIs.
- [ ] I understand what data is required before requesting weather.
- [ ] I understand what data is required before requesting World Bank data.
- [ ] I understand what data is required before requesting earthquake data.

### Phase 0 Gate

- [ ] I can explain the API flow without looking at the roadmap.
- [ ] I know what data I need from geocoding before requesting the other APIs.

---

# Phase 1 — Static UI

## HTML

- [ ] I created the basic HTML structure.
- [ ] I used semantic HTML where appropriate.
- [ ] I created the city search section.
- [ ] I created the search-results section.
- [ ] I created the selected-city section.
- [ ] I created the current-weather section.
- [ ] I created the 7-day forecast section.
- [ ] I created the country-intelligence section.
- [ ] I created the earthquake section.
- [ ] I created the saved-cities section.
- [ ] I created the compare-cities section.

## CSS

- [ ] I created the initial dashboard layout.
- [ ] I used Flexbox and/or Grid appropriately.
- [ ] I established spacing and readable typography.
- [ ] I created basic responsive behavior.
- [ ] The layout works on desktop.
- [ ] The layout works on a narrow/mobile viewport.
- [ ] There is no obvious horizontal overflow.
- [ ] Text does not break the layout.

## Fake Data

- [ ] I populated the UI with fake data.
- [ ] The dashboard looks like a real product before API integration.
- [ ] Search results have a believable structure.
- [ ] Weather data has a believable structure.
- [ ] Forecast cards have a believable structure.
- [ ] Country data has a believable structure.
- [ ] Earthquake data has a believable structure.

### Phase 1 Gate

- [ ] All major sections exist.
- [ ] The static dashboard is usable.
- [ ] The layout works on mobile.
- [ ] I can explain the purpose of every major UI section.

---

# Phase 2 — Search City

## Search Flow

- [ ] I created the search form.
- [ ] I connected the form to an event handler.
- [ ] I prevent the default form submission behavior where needed.
- [ ] I read the user's search input.
- [ ] I trim unnecessary whitespace.
- [ ] I validate empty input.
- [ ] I build the geocoding request correctly.
- [ ] I use `fetch()`.
- [ ] I parse the JSON response.
- [ ] I inspect the returned data before rendering it.
- [ ] I normalize search results.

## Search Result Shape

- [ ] Each result contains a city/name.
- [ ] Each result contains a country.
- [ ] Each result contains a country code.
- [ ] Each result contains latitude.
- [ ] Each result contains longitude.
- [ ] Each result contains timezone where available.
- [ ] I preserve useful administrative-region information where appropriate.

## UI States

- [ ] Empty search is handled.
- [ ] Loading state is shown.
- [ ] API failure is handled.
- [ ] Zero results are handled.
- [ ] Search results are rendered dynamically.
- [ ] Repeated searches work correctly.

## Testing

- [ ] Tokyo works.
- [ ] London works.
- [ ] Delhi works.
- [ ] New York works.
- [ ] An ambiguous city name was tested.
- [ ] Springfield or another repeated city name was tested.
- [ ] A garbage/nonexistent query was tested.
- [ ] Whitespace-only input was tested.

### Phase 2 Gate

- [ ] I can search for a city and see useful results.
- [ ] I understand the difference between raw API data and normalized application data.

---

# Phase 3 — Select Location

## Selection

- [ ] I can click/select a search result.
- [ ] The selected location is stored separately from search results.
- [ ] I have a clear `selectedCity` concept.
- [ ] The selected city contains its name.
- [ ] The selected city contains its country.
- [ ] The selected city contains its country code.
- [ ] The selected city contains latitude.
- [ ] The selected city contains longitude.
- [ ] The selected city contains timezone where available.
- [ ] Administrative region is handled where useful.

## Behavior Testing

- [ ] Selecting an ambiguous result works.
- [ ] Selecting different cities works.
- [ ] Missing administrative region does not break the UI.
- [ ] Editing the search input after selecting a city does not corrupt the selected city.
- [ ] Repeated city selections work.

### Phase 3 Gate

- [ ] I can clearly explain the difference between `searchResults` and `selectedCity`.
- [ ] All later API requests can use the selected city's coordinates/code.

---

# Phase 4 — Current Weather

## API Integration

- [ ] I request weather using the selected city's coordinates.
- [ ] I use the Open-Meteo Forecast API correctly.
- [ ] I parse the JSON response.
- [ ] I inspect the raw response.
- [ ] I normalize the weather data before rendering.

## Current Weather UI

- [ ] Current temperature is displayed.
- [ ] Feels-like temperature is displayed where useful.
- [ ] Humidity is displayed where useful.
- [ ] Precipitation information is displayed where useful.
- [ ] Wind information is displayed.
- [ ] Weather code is interpreted.
- [ ] Day/night information is handled where useful.

## Weather Codes

- [ ] I researched the weather-code mapping.
- [ ] I convert weather codes into meaningful UI text/icons/labels.
- [ ] Unknown/unhandled codes do not break the UI.

## Testing

- [ ] I tested more than one city.
- [ ] I tested slow network behavior.
- [ ] I tested changing cities quickly.
- [ ] I handled weather API failure.
- [ ] I handled missing/unexpected weather data.

### Phase 4 Gate

- [ ] Selecting a city produces correct current-weather data.
- [ ] Weather rendering does not depend directly on unexplained raw API structure.

---

# Phase 5 — 7-Day Forecast & Statistics

## Forecast Transformation

- [ ] I inspected the forecast's parallel arrays.
- [ ] I understand why parallel arrays need transformation.
- [ ] I transformed forecast arrays into one object per day.
- [ ] Each forecast-day object contains the needed date/data.
- [ ] The renderer receives the transformed forecast array.
- [ ] The renderer does not depend on the raw parallel-array structure.

## Forecast UI

- [ ] I render all 7 forecast days.
- [ ] Each day has readable date information.
- [ ] Each day displays the useful weather values.
- [ ] The forecast remains usable on mobile.

## Statistics

- [ ] I calculate the hottest day.
- [ ] I calculate the coldest day.
- [ ] I calculate average maximum temperature.
- [ ] I calculate average minimum temperature.
- [ ] I calculate the highest precipitation probability where applicable.
- [ ] I use `reduce()` where it genuinely simplifies the calculation.
- [ ] Statistics come from data, not DOM text.

### Phase 5 Gate

- [ ] I can explain how raw forecast arrays became usable daily objects.
- [ ] I can explain why each statistic is derived from the data.

---

# Phase 6 — World Bank Country Data

## Country Lookup

- [ ] I use the selected city's country code.
- [ ] I understand that World Bank data is country-level.
- [ ] I request population data.
- [ ] I request GDP data.
- [ ] I understand the relevant indicators:
  - [ ] `SP.POP.TOTL`
  - [ ] `NY.GDP.MKTP.CD`

## Data Handling

- [ ] I inspect the World Bank response structure.
- [ ] I handle the World Bank response's nested data structure.
- [ ] I handle missing/null observations.
- [ ] I find the latest usable observation.
- [ ] I preserve the observation year.
- [ ] I normalize the country metrics.
- [ ] Population displays correctly.
- [ ] GDP displays correctly.

## Multiple Requests

- [ ] I understand why population and GDP can be requested independently.
- [ ] I understand `Promise.all()`.
- [ ] I use `Promise.all()` only after understanding the individual requests.
- [ ] A World Bank failure does not erase working weather data.

### Phase 6 Gate

- [ ] The dashboard can show population and GDP for the selected city's country.
- [ ] I understand how city data connects to country-level data.

---

# Phase 7 — USGS Earthquake Intelligence

## API Integration

- [ ] I use the selected city's latitude.
- [ ] I use the selected city's longitude.
- [ ] I understand the earthquake search radius.
- [ ] I understand the selected time window.
- [ ] I understand the magnitude/limit parameters.
- [ ] I document my chosen earthquake query rules.
- [ ] I request USGS GeoJSON data.
- [ ] I inspect the GeoJSON response structure.

## GeoJSON Understanding

- [ ] I understand `FeatureCollection`.
- [ ] I understand `features[]`.
- [ ] I understand earthquake `properties`.
- [ ] I understand earthquake `geometry`.
- [ ] I can extract coordinates correctly.

## Normalization

- [ ] Each earthquake has an ID.
- [ ] Each earthquake has magnitude.
- [ ] Each earthquake has place information.
- [ ] Each earthquake has time.
- [ ] Each earthquake has depth where available.
- [ ] Each earthquake has latitude.
- [ ] Each earthquake has longitude.

## Earthquake UI

- [ ] Earthquake count is displayed.
- [ ] Strongest earthquake is displayed.
- [ ] Average magnitude is displayed where appropriate.
- [ ] Earthquake events are rendered in a list/table/card structure.
- [ ] Zero earthquakes is treated as a valid result.

### Phase 7 Gate

- [ ] I can explain the complete USGS response structure.
- [ ] I can explain why an empty earthquake list is not an API error.

---

# Phase 8 — Clean Application State

## State Design

- [ ] I have a clear application-state concept.
- [ ] I understand what belongs in state.
- [ ] I understand what should remain UI-only.
- [ ] I have a clear `selectedCity`.
- [ ] I have a clear weather data location.
- [ ] I have a clear country data location.
- [ ] I have a clear earthquake data location.
- [ ] I have a clear filters location.
- [ ] I have a clear favorites/saved-cities location.
- [ ] I understand where cache information belongs.

## Source vs Derived Data

- [ ] I distinguish raw/source collections from filtered collections.
- [ ] I keep the original earthquake collection available.
- [ ] I store filters separately from earthquake source data.
- [ ] I derive visible earthquakes from source data + filters.
- [ ] I understand the difference between stored data and calculated data.

### Phase 8 Gate

- [ ] I can explain where every major piece of application data lives.
- [ ] I am no longer relying on scattered unrelated globals.

---

# Phase 9 — Filter, Sort & Derived Data

## Earthquake Filtering

- [ ] I created an All filter.
- [ ] I created a 2+ magnitude filter.
- [ ] I created a 3+ magnitude filter.
- [ ] I created a 4+ magnitude filter.
- [ ] I created a 5+ magnitude filter.
- [ ] I can filter local earthquake data without refetching the API.
- [ ] I understand that filtering should not destroy the original dataset.

## Earthquake Sorting

- [ ] I can sort strongest first.
- [ ] I can sort weakest first.
- [ ] I can sort newest first.
- [ ] I can sort oldest first.
- [ ] I avoid accidentally mutating the source array when sorting.

## Derived Statistics

- [ ] Earthquake statistics update after filtering.
- [ ] Count reflects the visible dataset.
- [ ] Strongest magnitude reflects the visible dataset.
- [ ] Average magnitude reflects the visible dataset where appropriate.

## Other Sorting

- [ ] Forecast can be sorted/selected by hottest/coldest where useful.
- [ ] Saved cities can be sorted A-Z.
- [ ] Saved cities can be sorted Z-A.

## Array Methods

- [ ] I used `map()` for transformation.
- [ ] I used `filter()` for filtering.
- [ ] I used `reduce()` for a meaningful calculation.
- [ ] I used `find()` for a meaningful lookup.
- [ ] I used `some()` for a meaningful existence check.
- [ ] I used `sort()` without corrupting source data.
- [ ] I did not use array methods only to “tick a box.”

### Phase 9 Gate

- [ ] Filtering is local.
- [ ] Sorting is local.
- [ ] Derived statistics update correctly.
- [ ] Source data remains intact.

---

# Phase 10 — Loading, Error & Empty States

## Async States

- [ ] I understand the difference between idle/loading/success/empty/error.
- [ ] Search has a loading state.
- [ ] Weather has a loading state.
- [ ] Country data has a loading/error state.
- [ ] Earthquake data has a loading/error/empty state.

## Error Handling

- [ ] I use `try/catch` appropriately.
- [ ] API failures do not crash the entire application.
- [ ] One failed API does not erase unrelated successful data.
- [ ] Errors are understandable to the user.
- [ ] Retry behavior is implemented where it makes sense.

## Empty States

- [ ] No search results has a clear message.
- [ ] No earthquakes has a clear message.
- [ ] Missing country data has a clear message.
- [ ] Missing weather data has a clear message where needed.

## Race Conditions

- [ ] I tested selecting one city and then another quickly.
- [ ] I understand that the first request can finish after the second.
- [ ] I checked for stale data appearing under the wrong city.
- [ ] I prevent stale responses from corrupting the current selected-city view.

### Phase 10 Gate

- [ ] The dashboard fails gracefully.
- [ ] Partial failure does not destroy unrelated working sections.
- [ ] I tested a race-condition scenario.

---

# Phase 11 — localStorage & Session Cache

## Saved Cities

- [ ] I can save a city.
- [ ] I can remove a saved city.
- [ ] Saved cities survive page refresh.
- [ ] Saved cities can be selected.
- [ ] Duplicate cities are prevented or handled.
- [ ] I use `some()` or another clear method for duplicate detection.
- [ ] I use `find()` or another clear method for retrieving a saved city.
- [ ] I store useful city metadata.
- [ ] I do not store unnecessarily huge API responses.

## localStorage Safety

- [ ] I handle empty storage.
- [ ] I handle malformed stored data.
- [ ] I handle old/unexpected stored data where appropriate.
- [ ] I can inspect stored data in DevTools.

## Session Cache

- [ ] I understand the difference between localStorage and in-memory cache.
- [ ] I created a clear cache strategy.
- [ ] I decided what datasets should be cached.
- [ ] I decided how cache keys are created.
- [ ] I decided whether data needs freshness rules.
- [ ] Reopening a previously loaded city can use cached data where appropriate.
- [ ] I tested Tokyo → London → Tokyo.
- [ ] I checked the Network panel to verify cache behavior.

### Phase 11 Gate

- [ ] Saved cities work after refresh.
- [ ] Session caching reduces unnecessary requests.
- [ ] I can explain why persistent storage and session cache are different.

---

# Phase 12 — Debounce & UX Improvements

## Debounced Search

- [ ] Normal submit-based search already works reliably.
- [ ] I understand why debounce should come after the basic search flow.
- [ ] I added debounced search only after the basic version was stable.
- [ ] Typing does not trigger an API request for every character.
- [ ] The request waits until typing pauses.
- [ ] I use a sensible minimum query length.
- [ ] Clearing the input clears suggestions/results appropriately.
- [ ] Stale search results do not remain visible incorrectly.
- [ ] Keyboard interaction works.

## Testing Debounce

- [ ] I tested rapid typing.
- [ ] I checked the Network panel.
- [ ] I confirmed unnecessary requests are reduced.
- [ ] I tested short queries.
- [ ] I tested empty input.

## UX Improvements

- [ ] Error messages are clearer.
- [ ] Loading feedback is clear.
- [ ] Empty states are clear.
- [ ] Retry behavior is usable.
- [ ] Recent searches are considered/implemented where useful.
- [ ] Search results are easy to select.
- [ ] Render logic is reused instead of duplicated unnecessarily.

### Phase 12 Gate

- [ ] Search feels responsive.
- [ ] Search does not flood the API.
- [ ] The UI clearly communicates what is happening.

---

# Phase 13 — Compare Cities & Final Polish

## Compare Cities

- [ ] I can select two known/saved cities for comparison.
- [ ] I reuse existing city data where possible.
- [ ] I avoid duplicating dashboard fetch logic.
- [ ] I can compare current temperature.
- [ ] I can compare average high/low where available.
- [ ] I can compare population.
- [ ] I can compare GDP.
- [ ] I can compare earthquake count.
- [ ] I can compare strongest earthquake.
- [ ] Comparison handles missing data gracefully.
- [ ] I use clear lookup logic such as `find()` where appropriate.

## Responsive Polish

- [ ] Desktop layout is polished.
- [ ] Tablet layout is usable.
- [ ] Mobile layout is usable.
- [ ] Flexbox/Grid are used intentionally.
- [ ] Responsive sizing is reasonable.
- [ ] Breakpoints are used only where useful.
- [ ] `minmax()` or similar responsive techniques are used where useful.
- [ ] There is no horizontal overflow.
- [ ] Long city names do not break the layout.
- [ ] Long earthquake descriptions do not break the layout.
- [ ] Buttons remain usable on small screens.
- [ ] Cards do not become unnecessarily cramped.

## Accessibility

- [ ] Form inputs have labels.
- [ ] Buttons have meaningful accessible names.
- [ ] Keyboard navigation works.
- [ ] Focus states are visible.
- [ ] Heading hierarchy is logical.
- [ ] Important information is not communicated by color alone.
- [ ] Contrast is readable.
- [ ] Loading states are understandable.
- [ ] Error states are understandable.
- [ ] Empty states are understandable.

### Phase 13 Gate

- [ ] Comparison works.
- [ ] Mobile layout is polished.
- [ ] Accessibility basics are handled.
- [ ] No major UX problems remain.

---

# Final Testing Day

## Search Testing

- [ ] Normal city search works.
- [ ] Empty search works.
- [ ] Whitespace-only search works.
- [ ] Invalid search works.
- [ ] Ambiguous city search works.
- [ ] Repeated search works.
- [ ] Rapid search works.

## Location Testing

- [ ] Selecting a location works.
- [ ] Switching locations works.
- [ ] Coordinates remain correct.
- [ ] Country code remains correct.
- [ ] Timezone remains correct where available.

## Weather Testing

- [ ] Current weather works.
- [ ] Forecast works.
- [ ] Weather statistics work.
- [ ] Weather API failure is handled.
- [ ] Slow weather request is handled.
- [ ] Missing weather data is handled.

## Country Testing

- [ ] Population works.
- [ ] GDP works.
- [ ] Missing/null observations are handled.
- [ ] Country API failure does not break weather.

## Earthquake Testing

- [ ] Earthquake list works.
- [ ] Zero earthquakes works.
- [ ] One earthquake works.
- [ ] Many earthquakes work.
- [ ] Magnitude filters work.
- [ ] Sorting works.
- [ ] Statistics update after filtering.
- [ ] USGS failure is handled.

## Storage Testing

- [ ] Save city works.
- [ ] Remove city works.
- [ ] Refresh preserves saved cities.
- [ ] Duplicate saving is handled.
- [ ] Corrupted localStorage does not crash the app.
- [ ] Cache behavior is correct.

## Race Condition Testing

- [ ] I selected City A.
- [ ] I immediately selected City B.
- [ ] I checked whether City A's late response could overwrite City B.
- [ ] I fixed stale-response behavior if necessary.

## Responsive Testing

- [ ] Desktop tested.
- [ ] Tablet tested.
- [ ] Mobile tested.
- [ ] Narrow viewport tested.
- [ ] Wide viewport tested.
- [ ] Horizontal overflow checked.

## Network Testing

- [ ] Slow network tested.
- [ ] Failed network tested.
- [ ] API error tested.
- [ ] Network requests inspected in DevTools.

## Keyboard Testing

- [ ] Search can be used with keyboard.
- [ ] Search results can be navigated/selected appropriately.
- [ ] Buttons are keyboard accessible.
- [ ] Focus is visible.

---

# Debugging Checklist

When something breaks:

- [ ] I wrote down the expected behavior.
- [ ] I identified the actual behavior.
- [ ] I identified which pipeline is broken.
- [ ] I inspected the API response.
- [ ] I inspected the relevant state.
- [ ] I inspected the transformed data.
- [ ] I inspected the DOM/render step.
- [ ] I found where expected and actual behavior diverged.
- [ ] I changed one thing at a time.
- [ ] I tested again.
- [ ] I cleaned up the fix afterward.

## Debug Pipeline

- [ ] User action
- [ ] Event handler
- [ ] Validation
- [ ] API request
- [ ] Raw response
- [ ] Normalization/transformation
- [ ] State update
- [ ] Derived data
- [ ] Render

---

# Refactoring Checklist

Only refactor when the structure is becoming a problem.

- [ ] I checked for giant functions.
- [ ] I checked for repeated DOM manipulation.
- [ ] I checked for duplicated API logic.
- [ ] I checked for raw API objects being used everywhere.
- [ ] I checked for unnecessary globals.
- [ ] I checked for destructive filtering.
- [ ] I checked for accidental `.sort()` mutation.
- [ ] I checked for unnecessary API requests.
- [ ] I checked for stale data.
- [ ] I checked for mixed fetch/render responsibilities.
- [ ] I checked for unclear variable/function names.
- [ ] I checked for hard-coded city data.
- [ ] I removed only the duplication that actually hurts maintainability.
- [ ] I retested after refactoring.

---

# Final Skill Checklist

## HTML / CSS / UI

- [ ] Semantic HTML
- [ ] Forms
- [ ] DOM manipulation
- [ ] Events
- [ ] Responsive layout
- [ ] Flexbox
- [ ] Grid
- [ ] Mobile layout
- [ ] Accessibility basics
- [ ] Loading UI
- [ ] Error UI
- [ ] Empty UI

## JavaScript

- [ ] Variables and functions
- [ ] Arrays
- [ ] Objects
- [ ] Nested objects/arrays
- [ ] `map()`
- [ ] `filter()`
- [ ] `reduce()`
- [ ] `find()`
- [ ] `some()`
- [ ] `sort()`
- [ ] `Set`
- [ ] Destructuring
- [ ] Optional chaining
- [ ] Conditional logic
- [ ] DOM events
- [ ] Form validation

## APIs / Async JavaScript

- [ ] `fetch()`
- [ ] JSON
- [ ] `async/await`
- [ ] Promises
- [ ] `try/catch`
- [ ] `Promise.all()`
- [ ] API request parameters
- [ ] API response inspection
- [ ] API data normalization
- [ ] API error handling
- [ ] Multiple API requests
- [ ] Partial API failure handling
- [ ] Race-condition awareness

## Data Handling

- [ ] Raw API data vs application data
- [ ] Data normalization
- [ ] Derived data
- [ ] Statistics
- [ ] Filtering
- [ ] Sorting
- [ ] Nested response handling
- [ ] Parallel-array transformation
- [ ] GeoJSON structure
- [ ] Null/missing data handling

## Browser Storage / Performance

- [ ] localStorage
- [ ] Saved cities
- [ ] Duplicate prevention
- [ ] In-memory session cache
- [ ] Cache keys
- [ ] Cache behavior testing
- [ ] Debounced search
- [ ] Network inspection

## Development Skills

- [ ] Read API documentation
- [ ] Inspect responses before coding
- [ ] Use DevTools
- [ ] Debug systematically
- [ ] Test edge cases
- [ ] Test race conditions
- [ ] Refactor carefully
- [ ] Explain my own code
- [ ] Explain my data flow
- [ ] Explain my application state

---

# Milestone Tracker

## Milestone A — Search

- [ ] Static UI complete
- [ ] Search form complete
- [ ] Geocoding API connected
- [ ] Search results normalized
- [ ] Search results rendered
- [ ] Location selection works
- [ ] Search edge cases tested

**Milestone A complete:** [ ]

---

## Milestone B — Weather

- [ ] Current weather connected
- [ ] Weather normalized
- [ ] Weather rendered
- [ ] 7-day forecast connected
- [ ] Forecast transformed
- [ ] Forecast rendered
- [ ] Weather statistics calculated
- [ ] Weather loading/error states tested

**Milestone B complete:** [ ]

---

## Milestone C — Country + Earthquakes

- [ ] World Bank connected
- [ ] Population displayed
- [ ] GDP displayed
- [ ] Missing country data handled
- [ ] USGS connected
- [ ] Earthquakes normalized
- [ ] Earthquake list rendered
- [ ] Earthquake statistics calculated
- [ ] Earthquake filtering works
- [ ] Earthquake sorting works

**Milestone C complete:** [ ]

---

## Milestone D — Product Quality

- [ ] Application state cleaned up
- [ ] Loading states complete
- [ ] Error states complete
- [ ] Empty states complete
- [ ] Race conditions handled
- [ ] Saved cities work
- [ ] localStorage works
- [ ] Session cache works
- [ ] Debounced search works
- [ ] Compare cities works
- [ ] Responsive polish complete
- [ ] Accessibility basics complete
- [ ] Final testing complete
- [ ] Refactoring complete

**Milestone D complete:** [ ]

---

# Final Completion Gate

Before calling the project finished:

- [ ] I can build the project again without following the roadmap line-by-line.
- [ ] I understand the complete data flow.
- [ ] I understand the API responses I used.
- [ ] I understand my application state.
- [ ] I understand my transformations.
- [ ] I understand my filters and derived statistics.
- [ ] I understand my async requests.
- [ ] I understand my error/loading/empty states.
- [ ] I understand my localStorage implementation.
- [ ] I understand my cache.
- [ ] I understand my debounce implementation.
- [ ] I understand my comparison feature.
- [ ] I can debug a broken feature systematically.
- [ ] I can explain the project to another developer.
- [ ] I tested the project on desktop and mobile.
- [ ] I tested edge cases.
- [ ] I cleaned up unnecessary code.
- [ ] I did not add unnecessary libraries or architecture.

# PROJECT STATUS

**Current Phase:** ______________________________

**Current Milestone:** ___________________________

**Started:** _____________________________________

**Target Completion:** ___________________________

**Last Completed Task:** __________________________

**Current Blocker:** ______________________________

**Next Task:** ___________________________________

**Overall Progress:** ______ / ______

---

# Final Rule

> **Build → Test → Break → Debug → Clean → Continue**

Do not check a box because the code exists.

Check it only when:

**You built it + tested it + understand it.**
