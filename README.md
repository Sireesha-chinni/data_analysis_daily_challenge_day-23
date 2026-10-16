# Day 23 – Ola Defect Analysis (Python Strings Challenge)

A beginner-friendly Python coding challenge where complaint data from Ola rides is cleaned and analyzed using **only string operations** (no lists-of-dicts, no pandas, no regex).

## Scenario

You are a Data Analyst at Ola. Complaint data arrives as a single string, and you must clean and analyze it using string methods only.

## Input

```python
data = "Ride101-Ramesh-Late Arrival-Bangalore, Ride102-Suresh-rude behavior-Hyderabad, Ride103-Mahesh-Late arrival-Bangalore"
```

Each record follows the format:

```
RideID-DriverName-Issue-City
```

Records are separated by `, ` (comma + space).

## Files

| File | Description |
|------|-------------|
| `Day-23-Data-analytics-challenge-python.ipynb` | Jupyter Notebook with the solutions |
| `Day23Coding_Challenge.pdf` | Original challenge problem statement |
| `README.md` | This file |

## Tasks and Solutions

| # | Task | Approach | Result |
|---|------|----------|--------|
| 1 | Convert the string to lowercase | `data.lower()` | All text lowercased |
| 2 | Count total complaints | `data.count("ride")` | `3` |
| 3 | Count "late arrival" issues | `data.count("late")` | `2` |
| 4 | Count complaints from Bangalore | `data.count("bangalore")` | `2` |
| 5 | Extract first driver name | `data.split(",")[0].split("-")[1]` | `ramesh` |
| 6 | Standardize issue names | `data.replace(...)` | `rude_behavior`, `late_arrival` |

### Final cleaned string

```
ride101-ramesh-late_arrival-bangalore, ride102-suresh-rude_behavior-hyderabad, ride103-mahesh-late_arrival-bangalore
```

## String Methods Used

- `str.lower()` – normalize case
- `str.count()` – count occurrences of a substring
- `str.split()` – break the string into records and fields
- `str.replace()` – standardize issue names

## How to Run

1. Install Python 3.9+ and Jupyter:
   ```bash
   pip install notebook
   ```
2. Launch Jupyter and open the notebook:
   ```bash
   jupyter notebook Day-23-Data-analytics-challenge-python.ipynb
   ```
3. Run the cells from top to bottom (`Shift + Enter`).

## Notes and Possible Improvements

- **Task 3:** The solution counts `"late"`, which works for this data. A more precise version is `data.count("late arrival")`, which avoids false matches such as "late payment". Note this must run **before** Task 6, since after the replace the text becomes `late_arrival`.
- **Task 2:** Counting `"ride"` assumes the word never appears elsewhere. A safer alternative is `len(data.split(", "))`.
- **Task 1 ordering:** Lowercasing first is what makes the later counts and replacements case-insensitive.

## Key Takeaways

- Cleaning text first (lowercasing) makes later analysis consistent.
- `split()` is a quick way to parse delimited records.
- `replace()` is useful for standardizing messy categories into consistent labels.
