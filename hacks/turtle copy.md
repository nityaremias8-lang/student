---
layout: opencs
title: RPG
permalink: /exam
---

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Memory Game — AP CSP Project</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: #f5f5f5;
    color: #222;
    font-family: Arial, sans-serif;
    padding: 2rem;
  }

  .container {
    max-width: 520px;
    margin: 0 auto;
  }

  h1 { font-size: 1.8rem; margin-bottom: 0.25rem; }
  .subtitle { font-size: 0.85rem; color: #666; margin-bottom: 1.5rem; }

  /* Difficulty buttons */
  .mg-difficulty { display: flex; gap: 6px; margin-bottom: 1rem; }

  .diff-btn {
    font-size: 12px;
    padding: 5px 12px;
    border-radius: 4px;
    border: 1px solid #ccc;
    background: white;
    color: #444;
    cursor: pointer;
  }

  .diff-btn.active {
    background: #dbeafe;
    color: #1d4ed8;
    border-color: #93c5fd;
  }

  /* Stats row */
  .mg-stats { display: flex; gap: 12px; margin-bottom: 1rem; flex-wrap: wrap; }

  .mg-stat {
    background: #efefef;
    border-radius: 6px;
    padding: 0.5rem 1rem;
    font-size: 13px;
    color: #555;
  }

  .mg-stat span {
    font-size: 18px;
    font-weight: bold;
    color: #222;
    display: block;
  }

  /* Game board */
  #mg-board {
    display: grid;
    gap: 8px;
    margin-bottom: 1rem;
  }

  .mg-card {
    aspect-ratio: 1;
    border-radius: 6px;
    border: 1px solid #ccc;
    background: #e0e0e0;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 28px;
    user-select: none;
    transition: background 0.15s;
  }

  .mg-card.face-down .mg-card-inner { visibility: hidden; }

  .mg-card.flipped {
    background: white;
    border-color: #aaa;
    cursor: default;
  }

  .mg-card.matched {
    background: #dcfce7;
    border-color: #86efac;
    cursor: default;
  }

  .mg-card.wrong-flash { background: #fee2e2; border-color: #fca5a5; }

  /* Status message */
  #mg-msg {
    font-size: 14px;
    color: #555;
    min-height: 20px;
    margin-bottom: 0.75rem;
  }

  /* New game button */
  button.action-btn {
    font-size: 13px;
    padding: 6px 16px;
    border-radius: 4px;
    border: 1px solid #ccc;
    background: #f0f0f0;
    color: #333;
    cursor: pointer;
  }

  button.action-btn:hover { background: #e0e0e0; }
</style>
<body>
<div class="container">

  <h1>Memory Game</h1>
  <p class="subtitle">AP CSP Project — flip cards to find all matching pairs!</p>

  <!-- INPUT: difficulty selection triggers a new game -->
  <div class="mg-difficulty">
    <button class="diff-btn active" onclick="setDifficulty(4, 4, this)">Easy (4x4)</button>
    <button class="diff-btn"        onclick="setDifficulty(4, 5, this)">Medium (4x5)</button>
    <button class="diff-btn"        onclick="setDifficulty(5, 6, this)">Hard (5x6)</button>
  </div>

  <!-- OUTPUT: live stats -->
  <div class="mg-stats">
    <div class="mg-stat"><span id="mg-moves">0</span>moves</div>
    <div class="mg-stat"><span id="mg-pairs">0</span>pairs found</div>
    <div class="mg-stat"><span id="mg-total">0</span>total pairs</div>
  </div>

  <!-- OUTPUT: the card grid -->
  <div id="mg-board"></div>

  <!-- OUTPUT: match / win messages -->
  <div id="mg-msg"></div>

  <button class="action-btn" onclick="startGame()">New game</button>

</div>

<script>
// ─────────────────────────────────────────────────────────────
// DATA ABSTRACTION: cards is a list (array) of objects.
// Each object stores the card's symbol, whether it is flipped,
// and whether it has been matched.
//
// Using a single list means all rendering, match-checking, and
// win-detection can iterate the same structure — no parallel
// arrays or separate variables needed per card.
//
// flipped is a second list that tracks the (up to 2) currently
// face-up cards by their index in cards. Keeping this as a list
// makes it trivial to extend to 3-card variants without
// rewriting the rest of the program.
// ─────────────────────────────────────────────────────────────
const SYMBOLS = [
  "cat","dog","fish","bird","frog","bear",
  "fox","owl","bee","ant","bat","bug",
  "crab","duck","elk","fly"
];

const ICONS = {
  cat:"🐱", dog:"🐶", fish:"🐟", bird:"🐦",
  frog:"🐸", bear:"🐻", fox:"🦊", owl:"🦉",
  bee:"🐝",  ant:"🐜",  bat:"🦇",  bug:"🐛",
  crab:"🦀", duck:"🦆", elk:"🦌",  fly:"🪰"
};

let cards      = [];  // main list of all card objects
let flipped    = [];  // list of currently face-up card indices (max 2)
let moves      = 0;
let pairsFound = 0;
let totalPairs = 0;
let locked     = false; // prevents clicks while animating a wrong pair
let cols       = 4;
let rows       = 4;

// ─────────────────────────────────────────────────────────────
// STUDENT-DEVELOPED PROCEDURE: checkForMatch
// Name:        checkForMatch
// Parameters:  cardList    (Array) — the full cards list
//              flippedList (Array) — indices of the two face-up cards
// Return type: Object { matched: Boolean, won: Boolean }
//
// Purpose: Determines whether the two face-up cards share the
// same symbol (a match) and whether every pair on the board has
// been found (a win). Isolating this logic in one procedure
// means the matching rule is easy to find and change, and the
// event handler stays simple.
// ─────────────────────────────────────────────────────────────
function checkForMatch(cardList, flippedList) {
  // SEQUENCING: retrieve both cards, compare symbols, then check win

  let idxA  = flippedList[0];
  let idxB  = flippedList[1];
  let cardA = cardList[idxA];
  let cardB = cardList[idxB];

  // SELECTION: do the two face-up cards have the same symbol?
  let matched = cardA.symbol === cardB.symbol;

  let won = false;

  if (matched) {
    // ITERATION: scan every card in the list to check for a win
    let allMatched = true;
    for (let i = 0; i < cardList.length; i++) {
      // SELECTION: skip the two cards we just matched; check the rest
      if (i !== idxA && i !== idxB && !cardList[i].matched) {
        allMatched = false;
        break;
      }
    }
    won = allMatched;
  }

  return { matched: matched, won: won };
}

// ─────────────────────────────────────────────────────────────
// Fisher-Yates shuffle — randomizes an array in place
// ─────────────────────────────────────────────────────────────
function shuffle(arr) {
  for (let i = arr.length - 1; i > 0; i--) {
    let j   = Math.floor(Math.random() * (i + 1));
    let tmp = arr[i];
    arr[i]  = arr[j];
    arr[j]  = tmp;
  }
  return arr;
}

// ─────────────────────────────────────────────────────────────
// Builds the cards list for the chosen grid dimensions
// ─────────────────────────────────────────────────────────────
function buildCards(r, c) {
  totalPairs = Math.floor((r * c) / 2);

  // Pick random symbols, duplicate them to make pairs, then shuffle
  let pool  = shuffle(SYMBOLS.slice()).slice(0, totalPairs);
  let pairs = shuffle(pool.concat(pool));

  // ITERATION: create one card object per cell in the grid
  let list = [];
  for (let i = 0; i < pairs.length; i++) {
    list.push({ symbol: pairs[i], flipped: false, matched: false });
  }
  return list;
}

// ─────────────────────────────────────────────────────────────
// OUTPUT: renders the board by iterating over the cards list
// ─────────────────────────────────────────────────────────────
function renderBoard() {
  const board = document.getElementById("mg-board");
  board.style.gridTemplateColumns = `repeat(${cols}, 1fr)`;
  board.innerHTML = "";

  // ITERATION: create one DOM element for each card in the list
  for (let i = 0; i < cards.length; i++) {
    let c   = cards[i];
    let div = document.createElement("div");

    // SELECTION: assign CSS class based on the card's current state
    if (c.matched) {
      div.className = "mg-card matched";
    } else if (c.flipped) {
      div.className = "mg-card flipped";
    } else {
      div.className = "mg-card face-down";
      // INPUT: attach click handler only to face-down, unmatched cards
      div.addEventListener("click", (function(idx) {
        return function() { handleFlip(idx); };
      })(i));
    }

    div.innerHTML = `<span class="mg-card-inner">${ICONS[c.symbol]}</span>`;
    board.appendChild(div);
  }

  // OUTPUT: update the stat counters
  document.getElementById("mg-moves").textContent = moves;
  document.getElementById("mg-pairs").textContent = pairsFound;
  document.getElementById("mg-total").textContent = totalPairs;
}

// ─────────────────────────────────────────────────────────────
// INPUT: handles a card flip triggered by user click
// ─────────────────────────────────────────────────────────────
function handleFlip(idx) {
  if (locked)               return; // waiting to hide a wrong pair
  if (cards[idx].flipped)   return; // already face-up
  if (cards[idx].matched)   return; // already matched
  if (flipped.length >= 2)  return; // two cards already showing

  // Flip the card and add its index to the flipped list
  cards[idx].flipped = true;
  flipped.push(idx);
  renderBoard();

  // Evaluate only once two cards are face-up
  if (flipped.length === 2) {
    moves++;
    locked = true;

    // CALL TO STUDENT-DEVELOPED PROCEDURE
    const result = checkForMatch(cards, flipped);

    if (result.matched) {
      // Mark both cards matched in the list
      cards[flipped[0]].matched = true;
      cards[flipped[1]].matched = true;
      pairsFound++;
      flipped = [];
      locked  = false;
      renderBoard();

      // OUTPUT: win or continue message
      if (result.won) {
        document.getElementById("mg-msg").textContent =
          "You won! All pairs found in " + moves + " moves.";
      } else {
        document.getElementById("mg-msg").textContent = "Match! Keep going.";
      }

    } else {
      // OUTPUT: flash wrong cards red, then flip them back over
      document.getElementById("mg-msg").textContent = "No match — try again.";
      let idxA = flipped[0];
      let idxB = flipped[1];

      // Briefly add wrong-flash class for visual feedback
      const board = document.getElementById("mg-board");
      if (board.children[idxA]) board.children[idxA].classList.add("wrong-flash");
      if (board.children[idxB]) board.children[idxB].classList.add("wrong-flash");

      setTimeout(function() {
        cards[idxA].flipped = false;
        cards[idxB].flipped = false;
        flipped = [];
        locked  = false;
        renderBoard();
      }, 900);
    }
  }
}

// ─────────────────────────────────────────────────────────────
// Sets difficulty and starts a fresh game
// ─────────────────────────────────────────────────────────────
function setDifficulty(r, c, btn) {
  rows = r;
  cols = c;
  document.querySelectorAll(".diff-btn").forEach(function(b) {
    b.classList.remove("active");
  });
  btn.classList.add("active");
  startGame();
}

// ─────────────────────────────────────────────────────────────
// Starts (or restarts) a game — resets all state
// ─────────────────────────────────────────────────────────────
function startGame() {
  cards      = buildCards(rows, cols); // rebuild the cards list
  flipped    = [];
  moves      = 0;
  pairsFound = 0;
  locked     = false;
  document.getElementById("mg-msg").textContent = "";
  renderBoard();
}

// Start the first game when the page loads
startGame();
</script>
</body>
