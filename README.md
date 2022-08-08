# Front-End recruitment task
Welcome to Simployer! If you read this page it means that you'd like to join our team and we need to verify your skills in JavaScript and React technology. Read all the instructions first and then proceed with completing the task.

## Setup
1. Clone this repository
2. Crate a new branch out of `main` branch with your name e.g. `task/sebastian-kreft`
3. Install the project and start development, according to the criteria listed below.
4. Try to keep your code clean and use all the `git` features as you normally would in a team (commits, branches, pull requests)

## Instructions
Our users need a small analytics app, that will compare the daily pageview of these 3 Wikipedia articles:
 - https://en.wikipedia.org/wiki/The_Matrix
 - https://en.wikipedia.org/wiki/Spider-Man
 - https://en.wikipedia.org/wiki/Daft_Punk

Use this api to get the data:

```http request
https://wikimedia.org/api/rest_v1/metrics/pageviews/per-article/en.wikipedia/all-access/all-agents/<ARTICLE NAME>/daily/<START DATE>/<END_DATE>
```

for example:
```http request
https://wikimedia.org/api/rest_v1/metrics/pageviews/per-article/en.wikipedia/all-access/all-agents/Spider-Man/daily/20220101/20220130
```

### Requirements
1. User can read the data on a Chart
   1. Each article is a separate Series
   2. Arguments are dates, Values are the number of views
2. User can read the data as a DataGrid
   1. Each column represent a single article
   2. Each row represent a timestamp
   3. Cells contain page views
3. User can change the start date and end date in DropdownBoxes with Calendars
   1. Filters are global - they should reload both Chart and DataGrid
   2. There is an "Apply" button for filters that triggers fetching fresh data for selected filters
4. User can navigate between the two types of data presentation
   1. There is a Menu with 2 items: Chart, Data Grid
   2. Each menu item should lead to a separate route, where Chart and Data Grid will be shown separately, under their own URLs
   3. Filters are still global - when I choose one date range, it applies also after I switch to another route
5. API requests should be cached for 1 hour for the same date range
6. Add tests:
   1. Filter component should apply selected date after "Apply" button is clicked
   2. After Navigation item is clicked, the proper component should appear in the document

#### Sketches

![Page 1](./Screenshot%202022-08-08%20144253.jpg)

![Page 2](./Screenshot%202022-08-08%20144307.jpg)

### Assumptions
   1. Use DevExtreme library for Chart, DataGrid and DropdownBoxes with Calendars components
      1. https://js.devexpress.com/Documentation/Guide/React_Components/DevExtreme_React_Components/
      2. https://js.devexpress.com/Documentation/ApiReference/UI_Components/
   2. Do NOT focus on styling. Fell free to use any 3rd party components library to compose a simple layout and navigation
   3. For routing use: https://reactrouter.com/docs/en/v6
   4. For API request use a library of your choice or just use plain `fetch`
   5. For caching use https://tanstack.com/query/v4/?from=reactQueryV3&original=https://react-query-v3.tanstack.com/ or similar.
   6. For testing use:
      1. https://jestjs.io/
      2. https://testing-library.com/docs/