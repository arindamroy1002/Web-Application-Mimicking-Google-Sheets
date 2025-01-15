# Google Sheets Web Application

## Overview
This project is a simplified web-based spreadsheet application inspired by Google Sheets. It provides a grid-like interface for users to input data, perform calculations, and apply various mathematical functions. The core features include data entry, formula support, cell selection, and basic function calculations like `SUM`, `AVERAGE`, `MIN`, and `MAX`.

---

## Features

### 1. Grid Initialization
- The spreadsheet has a grid of 100 rows by 100 columns.
- Row and column headers are initialized using numerical indices (rows) and alphabetical indices (columns).
- Default cell content is an empty string, and each cell has a default property of left-aligned text.

### 2. Cell Navigation and Selection
- `selectedCell` and `selectedCellRange` track the currently focused cell and selected range.
- Users can select cells using mouse clicks or arrow keys.
- `drawSelectedCellBorder` and `drawSelectedCellRange` handle the visual rendering of active and selected cells.

### 3. Formula Support
- Formulas begin with `=` and can reference other cells by name (e.g., `=A1+B1`).
- Supported functions include:
  - `SUM(range)`
  - `AVERAGE(range)`
  - `MIN(range)`
  - `MAX(range)`
- `isFormula` detects formula input.
- `executeFunctionExpr` parses and executes function expressions.
- `execute` replaces cell references with actual values and evaluates the expression.

### 4. Dependency Management
- `executionsDependentOnCell` tracks cells dependent on other cells.
- `recalculateDependents` updates dependent cells when a referenced cell is modified.
- Circular reference detection is implemented via `checkCycle`.

### 5. Mathematical Operations
- Functions for sum, average, min, and max calculations are defined:
  - `run_sum_func`
  - `run_avg_func`
  - `run_min_func`
  - `run_max_func`
- `run_min_max_func` is a helper for min and max operations.

### 6. Data Update
- `updateCellValue` sets a cell’s value and triggers recalculation of dependents.
- `resetTextInput` captures input from a text box, processes it, and updates the corresponding cell.

---

## Key JavaScript Functions

| Function                        | Description                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------|
| `create2DArray(N, M, defaultValue)` | Creates a 2D array of size N x M with an optional default value.                             |
| `numberToColumnName(num)`        | Converts a numeric column index to an alphabetical name (e.g., 1 to A, 27 to AA).             |
| `convertCellNameToRowCol(name)`  | Converts a cell name (e.g., A1) to row and column indices.                                    |
| `convertRowColToCellName(row, col)` | Converts row and column indices to a cell name.                                               |
| `executeFunctionExpr(expr)`      | Parses and executes supported functions in a formula expression.                              |
| `recalculateDependents(cellName)`| Updates all dependent cells recursively when a referenced cell is changed.                    |
| `checkCycle(cellName, startCellName)` | Detects circular references to prevent infinite loops in calculations.                        |
| `drawGrid()`                     | Renders the grid, selected cell, and cell ranges on the canvas.                               |

---

## Dependencies
- The `math.js` library (or equivalent) for evaluating mathematical expressions.
- Browser compatibility with modern JavaScript (ES6).

---

## Usage Instructions

1. Clone or download the project files.
2. Open the `index.html` in a web browser.
3. Click on a cell to select it. Use arrow keys to navigate.
4. Type data directly into the cell. Press `Enter` to apply.
5. Use formulas starting with `=` (e.g., `=A1+B1`, `=SUM(A1:A3)`).
6. Circular reference errors will trigger an alert.

---

## Future Enhancements
- Add more functions like `COUNT`, `TRIM`, `UPPER`, `LOWER`, `FIND_AND_REPLACE`.
- Implement saving and loading spreadsheets.
- Add undo/redo functionality.
- Enable drag-and-drop range selection.
- Include data visualization (charts).

---

## Acknowledgments
- Inspired by Google Sheets for its intuitive interface and functionality.
- Special thanks to the creators of `math.js` for expression evaluation.

---

