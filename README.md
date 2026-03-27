# KADO - Connect by Corners

A polyomino strategy board game playable on iPhone / smartphone / PC.
No external libraries required.

GitHub Pages: https://tetutetu214.github.io/blokus-game/

## How to Play

### Game Modes

| Mode | Description |
|------|-------------|
| 1P vs CPU | You vs 3 CPU opponents |
| LOCAL 4P | Local multiplayer (pass & play) |

### Board Sizes

| Size | Pieces per player | Coverage | Style |
|------|------------------|----------|-------|
| 14×14 | 12 (n=1-4 + 3 pentominoes) | 90% | Quick Game |
| 20×20 | 21 (n=1-5, standard) | 89% | Standard |
| 24×24 | 28 (n=1-5 + 7 hexominoes) | 91% | Deep Strategy |

### Characters

9 CPU characters with unique 16-bit pixel art. Choose any 3 as opponents (duplicates OK).

| Rank | Name | Type | Caption |
|------|------|------|---------|
| 1 | BLAZE | ATK | Relentless force |
| 2 | AEGIS | DEF | Unbreakable wall |
| 3 | CHAOS | RNG | Brilliant madness |
| 4 | SPIKE | ATK | Sharp striker |
| 5 | PROXY | DEF | Steady shield |
| 6 | GLITCH | RNG | Unpredictable |
| 7 | EMBER | ATK | Fading spark |
| 8 | ECHO | DEF | Faint signal |
| 9 | FLICKER | RNG | Static noise |

Rank 1 = strongest. Within the same type, color intensity indicates strength.

### Controls

1. Select a piece from the panel below
2. **↻** Rotate / **↔** Flip
3. Tap the board to place (dots show valid positions)
4. **UNDO** to take back your last move
5. Auto-pass when no valid moves (toast notification)
6. **HOME** to save and return to title

### Rules

- Each player has a set of polyomino pieces
- First piece must touch your **corner**
- Subsequent pieces must connect **corner-to-corner** with your own
- Your pieces must **never share an edge**
- Touching other players' edges is OK
- Game ends when all players pass

### Scoring

- Remaining squares × -1 point
- All pieces placed = **+15 bonus**
- Highest score wins

## Features

- **3 Board Sizes**: 14×14 / 20×20 / 24×24 with mathematically balanced piece sets
- **9 CPU Characters**: Pixel art opponents with ATK/DEF/RNG personality axes
- **Per-Character Records**: Win rate and average score tracked per opponent
- **Match History**: Last 10 games rank/score graph
- **Save & Resume**: Browser saves game state automatically
- **Undo**: Take back your last placement
- **Auto Pass**: Automatic pass with notification when no moves available
- **Placement Dots**: Only valid corners are highlighted
- **All-CPU Highlight**: See where every CPU placed in the last round
- **Ghost Preview**: Hover (PC) or drag (mobile) to preview placement
- **Neon Arcade UI**: 90s arcade / pinball aesthetic with glow effects

## Architecture

```
index.html          ← HTML + CSS + UI logic (ES module)
js/
  game-logic.js     ← Pure game logic (no DOM dependencies)
  test-logic.js     ← Module unit tests (32 tests)
test.js             ← Legacy integration tests (79 tests)
```

Game logic is separated from UI for testability and future iOS app reuse.

## Running Locally

ES modules require a web server (file:// won't work):

```bash
# Python
python3 -m http.server 9000

# Node.js
npx serve
```

Then open http://localhost:9000

## Tests

```bash
# Integration tests
node test.js        # 79 tests

# Module unit tests
node js/test-logic.js   # 32 tests
```

## Tech Stack

- HTML / CSS / JavaScript (ES modules)
- Canvas API for board rendering
- Touch events (iPhone Safari / Android Chrome)
- Mouse hover preview (PC)
- localStorage for game saves & match records
- CPU AI: Weighted scoring with ATK/DEF/RNG personality system
- Colorblind-friendly palette (CUD compliant)
