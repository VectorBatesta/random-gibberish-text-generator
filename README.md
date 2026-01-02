# Random Script Text Generator

Generate batches of randomized **pseudo-text / gibberish** using selectable Unicode character dictionaries (scripts).

This tool is useful for:
- Font and Unicode rendering tests
- Procedural content generation
- Stress-testing text renderers
- Visual noise or placeholder text

---

## Features

- Selectable character dictionaries (`letters1`, `letters2`, `letters3`, …)
- Simple macro-style configuration
- Jittered output length for natural variability
- Word-like grouping with random spacing
- No external dependencies (Python 3.8+)

---

## Quickstart

1. Define one or more character sets in variables named `letters1`, `letters2`, `letters3`, etc.
2. Set `LETTERS_ID` to select which character set to use.
3. Run the script.

Example:
- `LETTERS_ID = 1` → uses `letters1`
- `LETTERS_ID = 2` → uses `letters2`

---

## Configuration

The generator is controlled through a small set of variables:

- **BASE_LETTERS**  
  Base target number of characters per output.

- **JITTER_RATIO**  
  Percentage of random variation applied to `BASE_LETTERS`.  
  For example, `0.8` means ±80% variation.

- **RUNS**  
  Number of outputs to generate.

- **LETTERS_ID**  
  Selects which character dictionary to use (`letters{ID}`).

- **RANDOM_SEED** (optional)  
  Set to a fixed integer for reproducible output.

---

## Length Jitter Logic

For each run, the total number of characters is chosen uniformly from this range:

- `BASE_LETTERS × (1 − JITTER_RATIO)`
- `BASE_LETTERS × (1 + JITTER_RATIO)`

The minimum value is clamped to at least **1** to prevent empty output.

---

## Output Behavior

- Text is generated in word-like chunks.
- Each “word” contains 5–10 characters.
- Words are separated by single spaces.
- The final output length respects the jittered character limit.

The result looks like structured nonsense rather than a single unbroken string.

---

## Usage Notes

- Add new scripts by defining new variables (`letters3`, `letters4`, etc.).  
  No changes to generator logic are required.
- For reproducible output (tests, comparisons), set `RANDOM_SEED`.
- For very large outputs, consider streaming to a file instead of printing to stdout.
- Character weighting or mixed scripts can be added by changing the selection logic.

---

## License

MIT License.
