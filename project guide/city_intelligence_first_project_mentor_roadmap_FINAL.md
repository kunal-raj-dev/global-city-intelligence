# City Intelligence --- First Project Mentor Roadmap

> **Purpose:** Build your first serious frontend application with HTML,
> CSS, and Vanilla JavaScript while learning how to investigate, debug,
> structure, and finish a real project independently.
>
> **Important:** This is **not a tutorial** and contains **no
> implementation code**. It tells you what to build, what to
> investigate, what to test, and what to understand. The implementation
> is yours.

------------------------------------------------------------------------

# 1. What You Are Building

## Global City Intelligence Dashboard

The user should be able to:

-   search for a city
-   choose the exact location from multiple matches
-   view current weather
-   view a 7-day forecast
-   see weather statistics
-   see country population and GDP
-   see nearby earthquake activity
-   filter and sort earthquake data
-   save cities
-   revisit cities efficiently through session caching
-   compare two cities
-   use the application comfortably on desktop and mobile

The final data flow is:

``` text
SEARCH CITY
    ↓
GEOCODING
    ↓
SELECT LOCATION
    ↓
SELECTED CITY
    ↓
 ┌──────────────┬──────────────┬──────────────┐
 ↓              ↓              ↓
WEATHER      WORLD BANK       USGS
 ↓              ↓              ↓
normalize     normalize      normalize
 └──────────────┬──────────────┘
                ↓
          APPLICATION STATE
                ↓
       filter / sort / calculate
                ↓
             RENDER
```

Do **not** build the final dashboard in one attempt.

Build one working version at a time.

------------------------------------------------------------------------

# 2. Learning Rules

These rules apply to the entire project.

## Rule 1 --- Try before asking

When stuck:

1.  State what you expected.
2.  Inspect the relevant data.
3.  Make an attempt.
4.  Read the error.
5.  Change something based on evidence.
6.  Test again.
7.  Only then ask for help.

Prefer asking:

> "Do not solve this. Give me one hint about what I should inspect."

Then ask for another hint if necessary.

------------------------------------------------------------------------

## Rule 2 --- Never paste code you cannot explain

For every meaningful block, know:

-   what problem it solves
-   what input it uses
-   what output/effect it produces
-   what would break if it were removed
-   why it belongs there

If you cannot explain it, slow down.

------------------------------------------------------------------------

## Rule 3 --- Raw API data is not application state

Think:

``` text
API RESPONSE
    ↓
inspect
    ↓
extract
    ↓
normalize
    ↓
application-friendly data
    ↓
filter / sort / calculate
    ↓
render
```

Do not allow API response shapes to control your whole application.

------------------------------------------------------------------------

## Rule 4 --- Keep responsibilities clear

As the project grows, mentally separate:

``` text
GET DATA
TRANSFORM DATA
UPDATE STATE
CALCULATE DERIVED DATA
RENDER UI
HANDLE EVENTS
PERSIST DATA
```

You do **not** need React, Redux, classes, advanced OOP, design
patterns, or a complex architecture.

------------------------------------------------------------------------

## Rule 5 --- Build one working version at a time

Never have five unfinished systems open simultaneously.

At every major phase, the application should still work.

------------------------------------------------------------------------

# 3. Allowed Stack

Use:

-   HTML
-   CSS
-   Vanilla JavaScript
-   `fetch()`
-   `async/await`
-   Promises
-   `try/catch`
-   arrays and objects
-   `map()`
-   `filter()`
-   `reduce()`
-   `find()`
-   `some()`
-   `sort()`
-   `Set`
-   destructuring
-   optional chaining
-   event listeners
-   forms
-   `localStorage`
-   URL/query parameters
-   browser DevTools

Do not use:

-   React
-   TypeScript
-   Node.js
-   Express
-   databases
-   authentication
-   frontend frameworks
-   Redux/state libraries
-   complex classes/OOP
-   WebSockets
-   advanced design patterns

------------------------------------------------------------------------

# 4. API Stack

## Open-Meteo Geocoding

**Purpose:** Convert a city search into possible locations.

Official documentation:

https://open-meteo.com/en/docs/geocoding-api

Example:

``` text
https://geocoding-api.open-meteo.com/v1/search?name=Tokyo&count=5&language=en&format=json
```

You need information such as:

-   city name
-   country
-   country code
-   administrative region when available
-   latitude
-   longitude
-   timezone

------------------------------------------------------------------------

## Open-Meteo Forecast

**Purpose:** Get current weather and daily forecast from coordinates.

Documentation:

https://open-meteo.com/en/docs

Important learning point:

Daily weather can arrive as parallel arrays:

``` text
dates:        [day1, day2, day3]
max temps:    [31,   29,   32]
min temps:    [22,   21,   23]
rain chance:  [10,   60,   20]
```

You must transform these into useful frontend records.

------------------------------------------------------------------------

## World Bank Indicators

**Purpose:** Get country-level population and GDP.

Documentation:

https://datahelpdesk.worldbank.org/knowledgebase/articles/889392-about-the-indicators-api-documentation

Recommended indicators:

``` text
Population → SP.POP.TOTL
GDP        → NY.GDP.MKTP.CD
```

The important relationship is:

``` text
CITY
 ↓
country code
 ↓
WORLD BANK
```

The World Bank response has a different structure from Open-Meteo, so
inspect it rather than guessing.

------------------------------------------------------------------------

## USGS Earthquake Catalog

**Purpose:** Find earthquake events near the selected city.

API:

https://earthquake.usgs.gov/fdsnws/event/1/

Important parameters include:

-   latitude
-   longitude
-   maximum radius
-   start/end time
-   minimum magnitude
-   result limit
-   sorting

GeoJSON structure:

``` text
FeatureCollection
    ↓
features[]
    ↓
feature.properties
feature.geometry.coordinates
```

You must normalize this before using it throughout your application.

------------------------------------------------------------------------

# 5. Product Rules

Before coding, decide and write down:

  Decision                   First-project choice
  -------------------------- --------------------------------------
  Search                     Text form
  Initial search behavior    Submit-based
  Search results             About 5
  Exact location selection   Yes
  Weather                    Current + 7 days
  Country data               Population + GDP
  Earthquakes                Defined radius + defined time window
  Favorites                  Yes
  Session cache              Yes
  Debounced search           Later enhancement
  Comparison                 Final feature
  Map                        No
  Authentication             No
  Backend                    No

You may change a decision later.

The point is to stop inventing requirements while coding.

------------------------------------------------------------------------

# 6. Project Structure

Start simple:

``` text
project/
├── index.html
├── style.css
├── app.js
└── assets/
```

Do not split JavaScript into eight files before you have a real reason.

Refactor when the file becomes difficult to understand.

------------------------------------------------------------------------

# 7. THE BUILD ROADMAP

Keep this section beside you while coding.

``` text
0. UNDERSTAND + INSPECT APIs
        ↓
1. STATIC UI
        ↓
2. SEARCH CITY
        ↓
3. SELECT LOCATION
        ↓
4. CURRENT WEATHER
        ↓
5. 7-DAY FORECAST + STATISTICS
        ↓
6. WORLD BANK COUNTRY DATA
        ↓
7. USGS EARTHQUAKES
        ↓
8. CLEAN APPLICATION STATE
        ↓
9. FILTER + SORT + DERIVED DATA
        ↓
10. LOADING + ERROR + EMPTY STATES
        ↓
11. localStorage + SESSION CACHE
        ↓
12. DEBOUNCE + UX IMPROVEMENTS
        ↓
13. COMPARE CITIES + FINAL POLISH
```

**Do not move to the next phase until the current phase works.**

------------------------------------------------------------------------

# PHASE 0 --- Understand the Product and APIs

## Goal

Understand what you are building before writing API JavaScript.

## Do this

### Step 0.1 — Write the user journey

Write the user journey in plain language:

``` text
Open application
    ↓
Search city
    ↓
See possible locations
    ↓
Select location
    ↓
Load dashboard
    ↓
Weather
Country data
Earthquakes
    ↓
Save city
    ↓
Return to another city
    ↓
Compare cities
```

Do not think about JavaScript functions yet.

Think about what the user does and what the application should show.

### Step 0.2 — Draw a rough wireframe

Before writing the real HTML, sketch the main screen on paper or in a text file.

You only need rough boxes and labels.

Example:

``` text
┌─────────────────────────────────┐
│ CITY INTELLIGENCE               │
│                                 │
│ [ Search city........ ] [Search]│
├─────────────────────────────────┤
│ SEARCH RESULTS                  │
│ • Tokyo, Japan                  │
│ • Tokyo, USA                    │
├─────────────────────────────────┤
│ SELECTED CITY                   │
│ Tokyo, Japan                    │
├─────────────────────────────────┤
│ CURRENT WEATHER                 │
│ 24°C       Humidity ...         │
├─────────────────────────────────┤
│ 7-DAY FORECAST                  │
│ Mon | Tue | Wed | Thu | ...    │
├─────────────────────────────────┤
│ COUNTRY        │ ECONOMY        │
│ Population     │ GDP            │
├─────────────────────────────────┤
│ EARTHQUAKES                     │
│ Count | Strongest | Average     │
│ [Filter] [Sort]                 │
├─────────────────────────────────┤
│ SAVED CITIES                    │
├─────────────────────────────────┤
│ COMPARE CITIES                  │
└─────────────────────────────────┘
```

The wireframe is not a design assignment.

Do **not** spend time choosing colors, fonts, shadows, icons, or pixel-perfect spacing.

Its purpose is to answer:

> What exists, where does it go, and what information must the interface make room for?

### Step 0.3 — Sketch the important UI states

Make small sketches for:

``` text
INITIAL
→ Search city

SEARCHING
→ Loading...

RESULTS
→ Multiple city matches

SELECTED
→ Loading dashboard...

SUCCESS
→ Full dashboard

ERROR
→ Something failed

EMPTY
→ No results / No earthquakes
```

This is important because the application will not always look like the final success state.

### Step 0.4 — Identify data ownership

Write down which API provides each important piece of information.

| UI information | Source |
|---|---|
| city name | geocoding |
| country | geocoding |
| latitude | geocoding |
| longitude | geocoding |
| timezone | geocoding |
| temperature | weather |
| forecast | weather |
| population | World Bank |
| GDP | World Bank |
| earthquakes | USGS |

### Step 0.5 — Inspect all four APIs

Inspect all four APIs manually in the browser.

For each API, record:

- endpoint
- required inputs
- useful fields
- response structure
- arrays
- nested objects
- null values
- units
- coordinate format
- possible failure/empty behavior

For each API, record:

-   endpoint
-   required inputs
-   useful fields
-   response structure
-   arrays
-   nested objects
-   null values
-   units
-   coordinate format
-   possible failure/empty behavior

## Important questions

Answer these before continuing:

> What information from geocoding is required before weather can be
> fetched?

> What should the interface look like before any real data exists?

> What should the user see while data is loading, when there are no results,
> and when an API fails?

You should be able to explain the entire data flow and the purpose of your
wireframe before continuing.

## Do not move on until

- You can explain what each API contributes.
- You understand that city name alone is not enough for weather.
- You know where coordinates come from.
- You know which country identifier World Bank will need.
- You have manually inspected all four API response types.
- You have a rough wireframe for the main dashboard.
- You have sketched the important initial/loading/success/error/empty states.

------------------------------------------------------------------------

# PHASE 1 --- Static UI

## Goal

Build the dashboard structure with fake data.

No API calls.

## Sections

``` text
CITY INTELLIGENCE

Search
Search Results
Selected City
Current Weather
7-Day Forecast
Country Intelligence
Earthquake Activity
Saved Cities
Compare Cities
```

Use:

-   semantic HTML
-   real form
-   labels
-   buttons
-   headings
-   selects where appropriate

Create convincing fake data so you know where real data will eventually
go.

## CSS

Establish:

-   page max width
-   spacing system
-   typography hierarchy
-   card style
-   grid behavior
-   button/input style

Test:

-   desktop
-   tablet
-   narrow mobile

Do not waste time on visual perfection.

## Done when

-   every major section exists
-   fake data looks believable
-   keyboard can operate the search form
-   no horizontal mobile overflow
-   the layout has somewhere for every future feature

------------------------------------------------------------------------

# PHASE 2 --- Search City

## Goal

Turn a city name into real search results.

Flow:

``` text
form submit
    ↓
validate input
    ↓
geocoding API
    ↓
JSON
    ↓
normalize results
    ↓
render results
```

## Requirements

Handle:

-   empty input
-   whitespace-only input
-   loading
-   API failure
-   zero results
-   repeated searches
-   ambiguous cities

A successful result should become an application-friendly object such
as:

``` text
{
    name,
    country,
    countryCode,
    latitude,
    longitude,
    timezone
}
```

Add administrative region if useful.

Do not pass the raw API object throughout your application.

## Test

``` text
Tokyo
London
Delhi
New York
Springfield
zzzzzzzz
```

## Done when

Search works repeatedly and produces dynamic, distinguishable results.

------------------------------------------------------------------------

# PHASE 3 --- Select Location

## Goal

Turn one search result into the confirmed selected city.

You now have two different concepts:

``` text
searchResults
```

and

``` text
selectedCity
```

Do not mix them.

## Selected city should contain enough information for future requests

At minimum:

-   name
-   country
-   country code
-   latitude
-   longitude
-   timezone
-   administrative region if available

## Test

-   same city name in different countries
-   missing administrative region
-   repeated city changes
-   search again after selecting
-   edit search input after selection

Editing the search input must **not** silently change the selected city.

## Done when

A user can search, choose one exact location, and the application
clearly knows which location is selected.

------------------------------------------------------------------------

# PHASE 4 --- Current Weather

## Goal

Use selected coordinates to fetch current weather.

Flow:

``` text
selectedCity
    ↓
latitude + longitude
    ↓
Open-Meteo
    ↓
normalize useful values
    ↓
render current weather
```

Start with:

-   temperature
-   feels-like temperature
-   humidity
-   precipitation if useful
-   wind speed
-   weather code
-   day/night if useful

Do not request every variable the API provides.

Research the weather-code mapping yourself.

## Requirements

-   weather belongs to selected city
-   loading state
-   success state
-   error state
-   missing-value handling
-   changing city replaces old weather

## Test

Use DevTools throttling and switch cities quickly.

------------------------------------------------------------------------

# PHASE 5 --- 7-Day Forecast + Statistics

## Goal

Learn data transformation properly.

Open-Meteo can return parallel arrays.

Transform:

``` text
RAW ARRAYS
    ↓
one object per day
    ↓
forecast array
    ↓
forecast renderer
```

Each day should contain the information your UI needs, for example:

``` text
date
maxTemperature
minTemperature
precipitationProbability
weatherCode
```

## Important rule

The forecast renderer should receive the transformed forecast array, not
the raw API arrays.

## Calculate derived information

At minimum:

-   hottest day
-   coldest day
-   average maximum temperature
-   average minimum temperature
-   highest precipitation probability

Use `reduce()` meaningfully.

Do not calculate statistics from DOM text.

## Done when

You can explain exactly how the raw API arrays became your forecast
objects.

------------------------------------------------------------------------

# PHASE 6 --- World Bank Country Data

## Goal

Connect the selected city's country to country-level intelligence.

Flow:

``` text
selectedCity.countryCode
    ↓
World Bank
    ↓
population
GDP
    ↓
normalize
    ↓
render
```

Use:

``` text
SP.POP.TOTL
NY.GDP.MKTP.CD
```

Use a reasonable historical range.

## Important

World Bank values can be `null`.

Do not:

``` text
null → 0
```

Instead, find the latest usable observation.

Your application-friendly metric should conceptually contain:

``` text
metric
value
year
```

## Population and GDP

Implement both.

Look for real duplication only after both work. Then decide whether a
shared helper improves clarity.

Do not create a giant generic abstraction just to avoid a few repeated
lines.

## Concurrency

Population and GDP are independent requests.

After you understand them separately, experiment with concurrent
execution using `Promise.all()` where appropriate.

Understand why concurrency makes sense rather than using it just to tick
a box.

## Done when

Selecting a city produces its weather plus the corresponding country
population and GDP.

------------------------------------------------------------------------

# PHASE 7 --- USGS Earthquake Intelligence

## Goal

Work with a third API and a new data format.

Flow:

``` text
selectedCity
    ↓
latitude + longitude
    ↓
radius + time window
    ↓
USGS GeoJSON
    ↓
normalize
    ↓
earthquake records
    ↓
render
```

## First decide

Document:

-   radius
-   time window
-   minimum magnitude if any
-   maximum result count

There is no single universally correct product choice.

## Understand GeoJSON

Inspect:

``` text
FeatureCollection
    ↓
features[]
    ↓
properties
geometry
```

Normalize each event into something like:

``` text
{
    id,
    magnitude,
    place,
    time,
    depth,
    latitude,
    longitude
}
```

Verify GeoJSON coordinate order yourself.

## Render

Show:

-   event count
-   strongest event
-   average magnitude
-   earthquake list
-   event time
-   depth
-   place

## Important

Zero earthquakes is a valid result, not an API failure.

## Done when

Changing the selected city changes the earthquake dataset.

------------------------------------------------------------------------

# PHASE 8 --- Clean Application State

## Goal

Stop feature development temporarily and clean the architecture.

Your state should clearly represent what the application knows.

Conceptually:

``` text
appState
├── search
├── selectedCity
├── weather
├── country
├── earthquakes
├── filters
├── favorites
└── cache
```

Exact structure is yours.

## Important distinction

Separate source data from UI controls.

Example:

``` text
allEarthquakes
```

is different from:

``` text
minimumMagnitude
sortOrder
```

which produces:

``` text
visibleEarthquakes
```

Do not destroy your original data just because the user changed a
filter.

## Ask yourself

-   What city is selected?
-   What weather belongs to it?
-   What country data belongs to it?
-   What earthquake data belongs to it?
-   What is filtered?
-   What is saved?
-   What is cached?

If you cannot answer these by looking at your state, refactor.

------------------------------------------------------------------------

# PHASE 9 --- Filter + Sort + Derived Data

## Goal

Make the existing data interactive without unnecessary API requests.

## Earthquake filters

For example:

``` text
All
2+
3+
4+
5+
```

Filtering must happen locally:

``` text
allEarthquakes
    ↓
filter
    ↓
visibleEarthquakes
```

Changing the filter must **not** call USGS again.

## Statistics

Statistics must update from the visible/filtered collection.

For example:

-   count
-   strongest
-   average magnitude

## Sorting

Earthquakes:

-   strongest first
-   weakest first
-   newest first
-   oldest first

Forecast:

-   hottest
-   coldest

Saved cities:

-   A-Z
-   Z-A

Do not accidentally mutate the original arrays while sorting.

Use `map`, `filter`, `reduce`, `find`, `some`, `sort`, and `Set` where
they solve real problems.

Do not force methods into the project just for practice.

------------------------------------------------------------------------

# PHASE 10 --- Loading + Error + Empty States

## Goal

Turn the multi-API demo into a reliable application.

Each major asynchronous section should distinguish:

``` text
IDLE
 ↓
LOADING
 ↓
SUCCESS

or

LOADING
 ↓
ERROR

or

SUCCESS
 ↓
EMPTY
```

Examples:

``` text
Searching cities...
Loading weather...
Loading country data...
Loading earthquakes...
```

## Critical rule

One API failure must not destroy successful independent sections.

Example:

``` text
Weather        ERROR
Population     SUCCESS
GDP            SUCCESS
Earthquakes    SUCCESS
```

The dashboard should still show the successful sections.

## Important race-condition test

Try:

``` text
Select London
    ↓
requests begin
    ↓
immediately select Tokyo
    ↓
Tokyo requests begin
    ↓
London finishes later
```

Ask:

> Could London data accidentally appear inside Tokyo's dashboard?

This is a real frontend problem.

You do not need an advanced solution immediately. First understand and
reproduce the behavior.

## Done when

-   loading always terminates
-   errors are understandable
-   empty data is distinguished from failure
-   independent sections can succeed/fail independently
-   changing cities does not leave stale data under the wrong city

------------------------------------------------------------------------

# PHASE 11 --- localStorage + Session Cache

## Part A --- Saved Cities

The user should be able to:

-   save selected city
-   see saved cities after refresh
-   remove city
-   select a saved city
-   prevent duplicates

Store location information, not giant API responses.

Useful fields:

``` text
name
country
countryCode
latitude
longitude
timezone
```

Remember:

``` text
localStorage stores strings
```

Handle:

-   empty storage
-   malformed storage
-   old stored data
-   duplicate saves

Use `some()` or another clear method to detect duplicates.

A saved city already contains coordinates, so think about whether
geocoding is necessary again.

------------------------------------------------------------------------

## Part B --- Session Cache

Understand the difference:

``` text
localStorage
→ persistent across refresh
```

and:

``` text
JavaScript memory
→ disappears on refresh
```

Scenario:

``` text
Tokyo
 ↓
fetch data

London
 ↓
fetch data

Tokyo
 ↓
check cache first
```

Decide:

-   cache key
-   cached datasets
-   when cached data is considered usable

Do not build an industrial caching system.

Use DevTools Network to prove that revisiting a city avoids unnecessary
requests where appropriate.

------------------------------------------------------------------------

# PHASE 12 --- Debounce + UX Improvements

Only add debounce **after normal submit-based search is reliable**.

## Goal

Understand why rapidly firing events need control.

Conceptually:

``` text
P
 ↓
Pa
 ↓
Pat
 ↓
Patn
 ↓
Patna
 ↓
wait
 ↓
search
```

Instead of requesting after every keystroke.

## Requirements

-   minimum query length
-   loading feedback
-   empty input clears suggestions
-   no stale result list
-   keyboard still works
-   rapid typing does not flood the API

Watch the Network panel.

Your success metric is **actual request behavior**, not whether the UI
merely feels fast.

## UX improvements

Now improve:

-   clearer feedback
-   retry where useful
-   better empty states
-   better error messages
-   recent searches if desired
-   reusable render logic

Do not add features just to avoid difficult bugs.

------------------------------------------------------------------------

# PHASE 13 --- Compare Cities + Final Polish

## Part A --- City Comparison

This is the final major feature.

Choose two saved/known cities:

``` text
[ Tokyo ▼ ]   VS   [ London ▼ ]
```

Compare reusable metrics such as:

``` text
Current temperature
Average forecast high
Average forecast low
Population
GDP
Earthquake count
Strongest earthquake
```

Use existing cached/loaded data.

Do not create a second copy of the dashboard logic.

Use `find()` or another clear lookup method to retrieve the appropriate
city data.

------------------------------------------------------------------------

## Part B --- Responsive CSS

Now do the full visual pass.

### Desktop

-   coherent max width
-   clear dashboard grid
-   readable cards
-   useful spacing

### Tablet

-   columns collapse naturally
-   forecast remains usable
-   filters wrap correctly

### Mobile

-   no horizontal overflow
-   readable text
-   touch-friendly controls
-   cards stack logically
-   search remains usable
-   long city names do not break layout
-   forecast uses responsive layout or controlled horizontal scrolling

Practice:

-   Flexbox
-   Grid
-   `minmax()`
-   responsive breakpoints
-   relative units
-   max-width containers
-   gaps
-   overflow handling
-   text wrapping

------------------------------------------------------------------------

## Part C --- Accessibility

Check:

-   real label for search input
-   keyboard form submission
-   keyboard-accessible search results
-   descriptive button text
-   visible focus states
-   logical heading structure
-   errors communicated clearly
-   information not conveyed by color alone
-   readable contrast
-   understandable loading states
-   meaningful icon/image alternatives

You do not need perfect WCAG expertise.

Build correct habits.

------------------------------------------------------------------------

# 8. Final Testing Day

Do not add features.

Try to break the application.

## Search

-   empty input
-   spaces only
-   one character
-   unusual city name
-   accented characters
-   ambiguous city
-   nonexistent city
-   repeated search
-   rapid different searches

## Location

-   missing administrative region
-   same city name in different countries
-   long names
-   repeated city changes

## Weather

-   missing value
-   API error
-   slow network
-   rapid city switching

## Country data

-   null latest value
-   missing years
-   API failure
-   very large GDP
-   small country

## Earthquakes

-   zero events
-   one event
-   many events
-   missing magnitude/place if encountered
-   filter then sort
-   reset filters

## localStorage

-   empty storage
-   existing favorites
-   duplicate save
-   remove favorite
-   corrupted value
-   refresh

## UI

-   narrow mobile
-   wide desktop
-   slow network
-   offline mode after page load
-   keyboard-only navigation

------------------------------------------------------------------------

# 9. Debugging Framework

When something breaks, do not randomly edit code.

Use:

``` text
1. State expected behavior
        ↓
2. State actual behavior
        ↓
3. Identify the pipeline
        ↓
4. Inspect the data/state
        ↓
5. Find where expected ≠ actual
        ↓
6. Change one thing
        ↓
7. Test again
        ↓
8. Clean up
```

Example:

``` text
Expected:
Tokyo forecast appears after selecting Tokyo.

Actual:
Tokyo heading appears but London forecast remains.

Pipeline:
selection
↓
selectedCity
↓
weather request
↓
weather state
↓
forecast transformation
↓
render
```

Inspect each boundary.

Do not rewrite the whole project because one value is wrong.

------------------------------------------------------------------------

# 10. Refactoring Rules

Before calling the project finished, inspect for:

-   giant functions
-   repeated DOM manipulation
-   duplicated API logic
-   raw API objects passed everywhere
-   unnecessary global variables
-   filtering that destroys source arrays
-   sorting that mutates original data accidentally
-   unnecessary API requests
-   stale data after city changes
-   rendering logic mixed into data-fetching logic
-   unclear variable names
-   hard-coded city data

Do not refactor for style alone.

Refactor when the current structure makes the next change harder or
makes the code difficult to reason about.

------------------------------------------------------------------------

# 11. Final Skill Checklist

By the end, you should have genuinely practiced:

``` text
HTML
CSS
responsive layout
semantic HTML
forms
DOM manipulation
event listeners
input validation

fetch()
JSON
async/await
Promises
try/catch
Promise.all()

arrays
objects
nested data
map()
filter()
reduce()
find()
some()
sort()
Set
destructuring
optional chaining

data normalization
derived data
application state
loading states
error states
empty states
partial success

local filtering
localStorage
session caching
debounce
API documentation
DevTools debugging
edge-case testing
refactoring
accessibility
```

Do not force a method into the project just to tick a box.

Every technique should solve an actual problem.

------------------------------------------------------------------------

# 12. Milestones

## Milestone A --- Search

You can demonstrate:

-   search
-   ambiguous results
-   location selection
-   no results
-   API error
-   repeated searches

You can explain:

-   event flow
-   search state
-   selected city state
-   how a clicked result maps to data

------------------------------------------------------------------------

## Milestone B --- Weather

You can demonstrate:

-   current weather
-   7-day forecast
-   statistics
-   city switching
-   loading
-   weather error

You can explain:

-   coordinate dependency
-   parallel-array transformation
-   normalized forecast
-   derived statistics

------------------------------------------------------------------------

## Milestone C --- Country + Earthquakes

You can demonstrate:

-   population
-   GDP
-   missing country data
-   earthquake list
-   earthquake statistics
-   filtering
-   sorting
-   zero-event state

You can explain:

-   multiple API dependencies
-   World Bank response shape
-   GeoJSON normalization
-   partial failures

------------------------------------------------------------------------

## Milestone D --- Product Quality

You can demonstrate:

-   favorites survive refresh
-   duplicates are prevented
-   cache behavior works
-   debounce reduces requests
-   responsive mobile layout
-   keyboard usage
-   independent API errors

You can explain:

-   why favorites are stored
-   why live API responses are not blindly stored
-   cache vs persistence
-   application-state boundaries

------------------------------------------------------------------------

# 13. Final Architecture to Understand

Not code. Responsibilities.

``` text
USER ACTION
    ↓
EVENT HANDLER
    ↓
VALIDATE INTENT
    ↓
FETCH IF NEEDED
    ↓
RAW RESPONSE
    ↓
NORMALIZE / TRANSFORM
    ↓
UPDATE APPLICATION STATE
    ↓
DERIVE FILTERED / CALCULATED DATA
    ↓
RENDER RELEVANT SECTION
```

Whole application:

``` text
SEARCH
  ↓
GEOCODING
  ↓
SELECT LOCATION
  ↓
SELECTED CITY
  ↓
  ├──── WEATHER ───── normalize ────┐
  │                                  │
  ├──── WORLD BANK ── normalize ─────┤
  │                                  ├── DASHBOARD
  └──── USGS ──────── normalize ─────┘
                                     │
                              filters / stats
                                     │
                                   render
```

If you understand this by the end, the project succeeded.

------------------------------------------------------------------------

# 14. The One Rule to Remember

You do **not** need to remember this entire document while coding.

At any moment, ask only:

> **Which phase am I building right now, and does it work before I move
> forward?**

Build.

Test.

Break it.

Debug it.

Clean it.

Then move on.
