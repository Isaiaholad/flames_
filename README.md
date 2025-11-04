# FLAMES Calculator App

A fun web-based relationship compatibility calculator based on the popular FLAMES game.

## Table of Contents

- [Overview](#overview)
- [What is FLAMES?](#what-is-flames)
- [How to Use](#how-to-use)
- [How It Works](#how-it-works)
- [Algorithm Explanation](#algorithm-explanation)
- [Project Structure](#project-structure)
- [Technical Details](#technical-details)
- [Installation](#installation)
- [Browser Compatibility](#browser-compatibility)

## Overview

The FLAMES Calculator is a simple, lightweight web application that determines the relationship compatibility between two people based on their names. This nostalgic game has been a favorite among friends for generations, and this implementation brings it to the web with a clean, easy-to-use interface.

## What is FLAMES?

FLAMES is an acronym that stands for:
- **F**riends
- **L**overs
- **A**dmires
- **M**arriage
- **E**nemies
- **S**ecret Lovers

The game calculates which of these relationship types best describes the connection between two people based on the letters in their names.

## How to Use

1. Open `flames.html` in any web browser
2. Enter the first name in the "Enter Name 1" field
3. Enter the second name in the "Enter Name 2" field
4. Click the "Calculate" button
5. View the result showing the relationship status between the two names

### Example

```
Name 1: Alice
Name 2: Bob
Result: "Alice and Bob are LOVERS"
```

## How It Works

The FLAMES algorithm follows these steps:

1. **Input Two Names**: The user enters two names
2. **Remove Common Letters**: The algorithm removes all common letters between the two names (case-sensitive)
3. **Count Remaining Letters**: Count the total number of remaining unique letters
4. **Calculate Status**: Use the count to determine the relationship status based on modulo 6

## Algorithm Explanation

### Step-by-Step Process

1. **String Comparison** (`strrept` function):
   - Iterates through the first name
   - Keeps only letters that don't appear in the second name
   - Repeats for the second name
   - Concatenates unique letters from both names

2. **Status Determination** (`status` function):
   - Takes the length of the remaining unique letters
   - Uses modulo 6 to map to a relationship status:
     - `length % 6 === 0` → **SECRET LOVERS**
     - `length % 6 === 5 or length === 5` → **ENEMIES**
     - `length % 6 === 4 or length === 4` → **MARRIAGE**
     - `length % 6 === 3 or length === 3` → **ADMIRES**
     - `length % 6 === 2 or length === 2` → **LOVERS**
     - `length % 6 === 1 or length === 1` → **FRIENDS**

### Code Breakdown

#### `strrept(x, y, z)` Function
```javascript
function strrept(x, y, z) {
    for (let i = 0; i < x.length; i++) {
        if (y.indexOf(x[i]) === -1) {
            z += x[i];
        }
    }
    return z;
}
```
- **Parameters**:
  - `x`: Source string to filter
  - `y`: Reference string to compare against
  - `z`: Accumulator string (starts empty)
- **Returns**: String with characters from `x` that don't exist in `y`

#### `status(a)` Function
```javascript
function status(a) {
    if (a.length % 6 === 0) {
        return "SECRET LOVERS";
    } else if (a.length === 5 || a.length % 6 === 5) {
        return "ENEMIES";
    }
    // ... more conditions
}
```
- **Parameter**: `a` - String of unique remaining letters
- **Returns**: Relationship status string based on length

## Project Structure

```
flames_/
├── flames.html          # Main application file
├── docs/
│   └── index.html      # GitHub Pages documentation (same as flames.html)
├── .github/            # GitHub configurations
└── README.md           # This documentation file
```

## Technical Details

### Technologies Used
- **HTML5**: Structure and markup
- **CSS**: Inline styling (minimal)
- **Vanilla JavaScript**: Core logic and DOM manipulation
- **No Dependencies**: Pure HTML/CSS/JS with no external libraries

### Key Features
- Lightweight (single HTML file, ~2KB)
- No server-side processing required
- Works entirely in the browser
- Responsive input validation
- Simple and intuitive UI

### Browser Events
- **Click Event**: Triggers calculation when "Calculate" button is clicked
- **DOM Manipulation**: Updates results dynamically without page reload

### Input Validation
- Checks for empty inputs
- Displays "No entry" message if either name field is blank

## Installation

### Option 1: Direct Use
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/flames_.git
   cd flames_
   ```

2. Open `flames.html` in your browser:
   ```bash
   # On Linux/Mac
   open flames.html

   # On Windows
   start flames.html
   ```

### Option 2: Serve Locally
Using Python's built-in HTTP server:
```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```
Then visit `http://localhost:8000/flames.html`

### Option 3: GitHub Pages
The app is also available via GitHub Pages at:
```
https://yourusername.github.io/flames_/
```

## Browser Compatibility

This application is compatible with all modern browsers:
- Google Chrome (latest)
- Mozilla Firefox (latest)
- Safari (latest)
- Microsoft Edge (latest)
- Opera (latest)

**Minimum Requirements**: Any browser supporting ES6 JavaScript features

## Development

### Customization
You can easily customize the app by modifying:

1. **Relationship Statuses**: Edit the `status()` function to change outputs
2. **Algorithm Logic**: Modify the `strrept()` function for different letter matching rules
3. **Styling**: Add CSS to enhance the visual appearance
4. **Additional Features**: Add history tracking, animations, or social sharing

### Example Enhancement Ideas
- Add CSS styling for better UI/UX
- Implement case-insensitive matching
- Add animation effects for results
- Store calculation history
- Add share functionality
- Support for full names (first + last)
- Multiple language support

## License

This project is open source and available for personal and educational use.

## Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest new features
- Submit pull requests
- Improve documentation

## Credits

The FLAMES game is a classic relationship compatibility game that has been popular for decades. This is a modern web implementation of the traditional algorithm.

---

**Note**: This app is for entertainment purposes only. The results are generated algorithmically and should not be taken seriously! 🎮
