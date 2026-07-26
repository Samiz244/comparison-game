# Interactive Image Ranking App

A browser-based comparison game that ranks a collection of images using the Elo rating system. Each choice updates both competitors' ratings, and users can open a live leaderboard to see the current ordering.

## Features

- Pairwise image comparisons
- Elo-based rating updates after every selection
- Generation of all unique comparison pairs
- Live display of both competitors' current ratings
- Ranked leaderboard sorted by Elo score
- Responsive, event-driven interface with hover and click feedback
- No framework or build step required

## How the ranking works

Every image begins with a rating of `1000`. For each comparison, the app calculates the expected outcome using the standard Elo formula and applies a `K` factor of `32`:

```text
expected = 1 / (1 + 10 ^ ((opponentRating - currentRating) / 400))
newRating = currentRating + K * (actualScore - expected)
```

The selected image receives an actual score of `1`; the other receives `0`. Ratings are rounded and the leaderboard is re-sorted whenever it is opened.

## Technology

- JavaScript
- HTML5
- CSS3
- DOM events and dynamic rendering

## Run locally

```bash
git clone https://github.com/Samiz244/comparison-game.git
cd comparison-game
```

Open `index.html` in a browser, or serve the directory with a simple local server:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Project structure

```text
index.html       Page structure and comparison interface
hotNot.js        Pair generation, Elo calculations, and leaderboard logic
mashstyle.css    Responsive layout and interactions
photos/          Comparison images
```

## Future improvements

- Persist ratings between sessions
- Randomize or balance pair ordering
- Add keyboard and screen-reader support
- Separate ranking data from presentation logic
- Add automated tests for Elo calculations