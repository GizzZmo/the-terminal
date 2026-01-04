# The Terminal 🎮

> A cyberpunk-themed chess game featuring Matrix-style visuals and an AI opponent.

![Chess Game](https://img.shields.io/badge/Game-Chess-green) ![AI Level](https://img.shields.io/badge/AI-1500--1800%20ELO-brightgreen) ![License](https://img.shields.io/badge/License-Open%20Source-blue)

## 🎯 Overview

**The Terminal** is an interactive browser-based chess game that combines classic chess gameplay with a stunning cyberpunk aesthetic. Play against the GM 3000 AI in a neon-green Matrix-inspired environment.

### Features

- 🎨 **Cyberpunk Aesthetics**: High-contrast neon green on deep black with Matrix rain background
- 🤖 **Adaptive AI Opponent**: Multi-ply minimax with alpha-beta pruning, piece-square tables, opening book, and difficulty levels
- ♟️ **Full Chess Rules**: Complete move validation including castling, en passant, and pawn promotion
- 📊 **Real-time Evaluation**: Visual evaluation bar showing position advantage
- 📝 **Move History & Log**: Timestamped log plus structured move list with undo support
- 🔄 **Board Flip & Modes**: View from either side and switch between vs AI and two-player hot-seat
- 🕑 **Game Clock & Sound**: Dual timers, hints, PGN export, and toggleable audio cues
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
6. **Undo**: Step back one move (two plies in AI mode) with the **Undo** button
7. **Hint**: Request the AI's suggested move with **Hint**
8. **Export PGN**: Save/share the current game with **Export PGN**

### Game Rules

- You play as **White** and the AI plays as **Black** (unless in **2 PLAYERS** mode)
- Standard chess rules apply
- Pawns automatically promote to Queens when reaching the last rank
- The AI responds automatically after your move (AI mode)
- Game ends in checkmate, draw, or if a player runs out of time

### Visual Indicators

- **Green Highlight**: Currently selected piece
- **Yellow Border**: Last move made (from/to squares)
- **Green Glow**: Square hover effect
- **Cyan Outline**: Hint suggestion squares
- **Evaluation Bar**: Shows positional advantage (right = white winning, left = black winning)

### Modes & Difficulty

- **Mode Toggle**: Switch between **VS AI** and **2 PLAYERS** using the control panel
- **Difficulty Levels**: Easy (1-ply with added randomness), Medium (2-ply), Hard (3-ply) — all using alpha-beta pruning and piece-square tables
- **Opening Book**: Early moves leverage a lightweight opening book for more human-like play

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
Upgraded AI pipeline featuring:
- **Multi-ply Minimax + Alpha-Beta**: Depth varies by difficulty (1-3 plies)
- **Piece-Square Tables**: Positionally aware evaluation including endgame king tables
- **Opening Book**: Common opening lines for natural early play
- **Hints & Suggestions**: Re-uses the search to propose strong candidate moves

#### 4. UI Rendering
- **CSS Grid**: 8x8 board layout
- **Unicode Chess Pieces**: ♔ ♕ ♖ ♗ ♘ ♙ ♚ ♛ ♜ ♝ ♞ ♟
- **Dynamic Updates**: Board re-renders after each move
- **Responsive Design**: Adapts to screen size

### Code Organization

The codebase is organized into logical sections:

1. **CSS Styling** (Lines ~7-254):
   - Custom properties (CSS variables)
   - Layout and positioning
   - Component styling
   - Responsive breakpoints

2. **Matrix Rain Effect** (Lines ~301-360):
   - Canvas setup
   - Animation loop
   - Character rendering

3. **Chess Game State** (Lines ~362-378):
   - Game initialization
   - State variables
   - Piece mappings

4. **UI Helper Functions** (Lines ~380-408):
   - Logging system
   - Status updates

5. **Board Rendering** (Lines ~414-478):
   - Square creation
   - Piece placement
   - Highlighting logic

6. **Game Interaction** (Lines ~483-531):
   - Click handlers
   - Move validation
   - Turn management

7. **Game State Checking** (Lines ~537-544):
   - Checkmate detection
   - Draw detection
   - Status updates

8. **AI Engine** (Lines ~546-650):
   - Position evaluation
   - Move selection
   - AI response

9. **Utility Functions** (Lines ~655-689):
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

- Use the **Difficulty** dropdown (Easy/Medium/Hard) to switch search depth and randomness
- Tweak search parameters in `difficultySettings` (depth and randomness)
- Modify `pieceValues` or the piece-square tables (`pst`) to favor different styles

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

- **Auto-Promotion**: Pawns always promote to Queens (no choice of piece)
- **No Save/Load**: Games cannot be saved and resumed later

## 🚧 Future Enhancements

Potential improvements for future versions:

- [x] Multi-ply search depth (minimax/alpha-beta pruning)
- [x] Position evaluation (piece square tables)
- [x] Opening book integration
- [x] Move history with undo functionality
- [x] PGN export
- [x] Difficulty levels
- [x] Two-player mode
- [x] Game timer/clock
- [x] Sound effects
- [x] Move suggestions/hints

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
