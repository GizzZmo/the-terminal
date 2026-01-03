# The Terminal 🎮

> A cyberpunk-themed chess game featuring Matrix-style visuals and an AI opponent.

![Chess Game](https://img.shields.io/badge/Game-Chess-green) ![AI Level](https://img.shields.io/badge/AI-1500--1800%20ELO-brightgreen) ![License](https://img.shields.io/badge/License-Open%20Source-blue)

## 🎯 Overview

**The Terminal** is an interactive browser-based chess game that combines classic chess gameplay with a stunning cyberpunk aesthetic. Play against the GM 3000 AI in a neon-green Matrix-inspired environment.

### Features

- 🎨 **Cyberpunk Aesthetics**: High-contrast neon green on deep black with Matrix rain background
- 🤖 **AI Opponent**: GM 3000 AI using material evaluation (approximately 1500-1800 ELO strength)
- ♟️ **Full Chess Rules**: Complete move validation including castling, en passant, and pawn promotion
- 📊 **Real-time Evaluation**: Visual evaluation bar showing position advantage
- 📝 **Game Log**: Timestamped log of all moves and game events
- 🔄 **Board Flip**: View the game from either white's or black's perspective
- 📱 **Responsive Design**: Fully playable on desktop and mobile devices

## 🚀 Getting Started

### Quick Start

1. Clone this repository or download the files
2. Open `index.html` in any modern web browser
3. Start playing! Click on a piece to select it, then click on a destination square to move

### No Installation Required

This is a self-contained HTML file that requires no build process, dependencies installation, or server setup. Just open it in your browser and play!

### Requirements

- A modern web browser (Chrome, Firefox, Safari, Edge)
- JavaScript enabled
- Internet connection (for loading chess.js library from CDN)

## 🎮 How to Play

### Basic Controls

1. **Select a Piece**: Click on any of your pieces (white pieces)
2. **Make a Move**: Click on a valid destination square
3. **Deselect**: Click on the same piece again to deselect it
4. **Reset Game**: Click "Reset System" button to start a new game
5. **Flip Board**: Click "Flip Cam" to view from black's perspective

### Game Rules

- You play as **White** and the AI plays as **Black**
- Standard chess rules apply
- Pawns automatically promote to Queens when reaching the last rank
- The AI responds automatically after your move
- Game ends in checkmate or draw

### Visual Indicators

- **Green Highlight**: Currently selected piece
- **Yellow Border**: Last move made (from/to squares)
- **Green Glow**: Square hover effect
- **Evaluation Bar**: Shows material advantage (right = white winning, left = black winning)

## 🏗️ Technical Architecture

### Project Structure

```
the-terminal/
├── index.html          # Main game file (self-contained)
└── README.md          # This file
```

### Technology Stack

- **HTML5 Canvas**: For Matrix rain animation
- **CSS3**: For styling and responsive layout
- **JavaScript (ES6+)**: For game logic and UI
- **chess.js**: External library for chess rules and move validation

### Key Components

#### 1. Matrix Rain Effect
Creates the iconic falling character animation in the background using HTML5 Canvas with:
- Katakana, Latin, and numeric characters
- Semi-transparent trail effect
- Continuous animation at ~33fps

#### 2. Chess Engine Integration
Uses the chess.js library (v0.10.3) for:
- Move validation
- Game state management
- Check/checkmate/draw detection
- FEN string handling

#### 3. AI Implementation
Simple but effective AI using:
- **Material Evaluation**: Piece values (Pawn=10, Knight=30, Bishop=30, Rook=50, Queen=90, King=900)
- **1-Ply Search**: Evaluates all possible moves one level deep
- **Randomness Factor**: Adds variation to avoid predictable play
- **Greedy Selection**: Chooses move with best material outcome

#### 4. UI Rendering
- **CSS Grid**: 8x8 board layout
- **Unicode Chess Pieces**: ♔ ♕ ♖ ♗ ♘ ♙ ♚ ♛ ♜ ♝ ♞ ♟
- **Dynamic Updates**: Board re-renders after each move
- **Responsive Design**: Adapts to screen size

### Code Organization

The codebase is organized into logical sections:

1. **CSS Styling** (Lines ~7-230):
   - Custom properties (CSS variables)
   - Layout and positioning
   - Component styling
   - Responsive breakpoints

2. **Matrix Rain Effect** (Lines ~231-270):
   - Canvas setup
   - Animation loop
   - Character rendering

3. **Chess Game State** (Lines ~271-310):
   - Game initialization
   - State variables
   - Piece mappings

4. **UI Helper Functions** (Lines ~311-340):
   - Logging system
   - Status updates

5. **Board Rendering** (Lines ~341-400):
   - Square creation
   - Piece placement
   - Highlighting logic

6. **Game Interaction** (Lines ~401-460):
   - Click handlers
   - Move validation
   - Turn management

7. **Game State Checking** (Lines ~461-480):
   - Checkmate detection
   - Draw detection
   - Status updates

8. **AI Engine** (Lines ~481-550):
   - Position evaluation
   - Move selection
   - AI response

9. **Utility Functions** (Lines ~551-580):
   - Evaluation bar update
   - Game reset
   - Board flipping

## 🎨 Customization

### Changing Colors

Modify the CSS custom properties at the top of the `<style>` section:

```css
:root {
    --neon-green: #0f0;       /* Primary accent color */
    --dark-green: #053305;     /* Background highlights */
    --grid-color: #001a00;     /* Subtle elements */
}
```

### Adjusting AI Strength

Modify the piece values in the `pieceValues` object:

```javascript
const pieceValues = { p: 10, n: 30, b: 30, r: 50, q: 90, k: 900 };
```

Or adjust the randomness factor in the `aiMove()` function:

```javascript
boardValue += (Math.random() * 2) - 1; // Increase range for more randomness
```

### Board Size

Change the square size in the CSS:

```css
#board {
    grid-template-columns: repeat(8, 60px); /* Change 60px */
    grid-template-rows: repeat(8, 60px);
}

.square {
    width: 60px;  /* Change here too */
    height: 60px;
    font-size: 40px; /* Adjust piece size */
}
```

## 🐛 Known Limitations

- **AI Depth**: The AI only looks one move ahead (1-ply), making it beatable for experienced players
- **No Opening Book**: The AI doesn't use standard chess openings
- **No Endgame Tables**: Position evaluation is purely material-based
- **Auto-Promotion**: Pawns always promote to Queens (no choice of piece)
- **No Move History Navigation**: Cannot undo or review previous positions
- **No Save/Load**: Games cannot be saved and resumed later

## 🚧 Future Enhancements

Potential improvements for future versions:

- [ ] Multi-ply search depth (minimax/alpha-beta pruning)
- [ ] Position evaluation (piece square tables)
- [ ] Opening book integration
- [ ] Move history with undo functionality
- [ ] PGN export
- [ ] Difficulty levels
- [ ] Two-player mode
- [ ] Game timer/clock
- [ ] Sound effects
- [ ] Move suggestions/hints

## 📝 License

This project is open source and available for educational purposes. Feel free to modify and distribute.

## 🤝 Contributing

Contributions are welcome! Feel free to:

- Report bugs
- Suggest new features
- Submit pull requests
- Improve documentation

## 📧 Contact

For questions or feedback, please open an issue on GitHub.

---

**Enjoy the game! May your moves be swift and your strategy sound.** ♔

*"The only way to win is to learn to play." - GM 3000*
