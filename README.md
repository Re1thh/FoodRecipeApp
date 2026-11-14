# FoodRecipeApp

A small single-page React app that searches recipes by keyword using the Edamam Recipe Search API and shows the results as a grid of cards. It is one screen with a search box and a results list; there is no routing, no backend and no saved state.

Built in 2023 while learning React and Tailwind CSS.

## Features

- Search box and a Search button that query the Edamam recipe search endpoint with the typed keyword
- Results grid (up to 30 recipes) showing each recipe's image, meal type, name and total calories (rounded)
- The query also applies fixed filters set in code: a calorie range of 591-722 and the `alcohol-free` health label
- Responsive card layout using Tailwind utility classes (1, 2 or 4 columns depending on screen width)

## Stack

- React 18 (Create React App, `react-scripts` 5.0.1)
- Tailwind CSS 3
- Edamam Recipe Search API (called directly from the browser with `fetch`)

## Prerequisites

- Node.js and npm
- An Edamam developer account with an application ID and key for the Recipe Search API

## Configuration

The Edamam app ID and key are currently written directly in `src/App.js`. Replace them with your own values. A better setup is to move them into a `.env.local` file (ignored by git) and read them as `process.env.REACT_APP_EDAMAM_ID` / `process.env.REACT_APP_EDAMAM_KEY`. Note that any key used in a browser app is visible to users.

The code calls the older `https://api.edamam.com/search` endpoint. Edamam's current API is v2 (`/api/recipes/v2`), so the request may need updating to work today.

## How to run

```bash
npm install
npm start      # development server on http://localhost:3000
npm run build  # production build into build/
```

## Tests

`src/App.test.js` is the unchanged Create React App sample test. It looks for a "learn react" link that this app does not render, so `npm test` is expected to fail until the test is rewritten.

## Project structure

```
src/
  App.js        search input, Edamam request, holds results in state
  output.js     results grid (recipe cards)
  index.js      React entry point
  index.css     Tailwind directives
  safe.js       leftover static HTML card template (not imported)
tailwind.config.js
```
