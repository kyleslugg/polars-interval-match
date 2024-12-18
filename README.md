# Polars Interval Match

This package enables the matching of a Polars `Series` of numerical values (currently only `Float64` is supported) to a `Series` of interval strings (using standard interval notation).

## Installation

You can install the package using pip:

```sh
pip install polars-interval-match
```

## Usage

Here is a basic example of how to use the `match_intervals` function:

```python
import polars as pl
from polars_interval_match import match_intervals

# Create a Polars Series of values
values = pl.Series("values", [1.5, 2.5, 3.5, 4.5])

# Create a Polars Series of interval strings
intervals = pl.Series("intervals", ["[1.0, 2.0]", "(2.0, 3.0]", "[3.0, 4.0)", "(4.0, 5.0]"])

# Match values to intervals
matched = match_intervals(values, intervals)

# Show the result
print(matched)
```

The match_intervals function matches each value in the `values` Series to the corresponding interval in the `intervals` Series. The intervals are specified using standard interval notation:

- `[a, b]` denotes an interval that includes both endpoints a and b (is closed on both the left and the right).
- `(a, b]` denotes an interval that excludes the start point a but includes the endpoint b (is closed on the right only).
- `[a, b)` denotes an interval that includes the start point a but excludes the endpoint b (is closed on the left only).
- `(a, b)` denotes an interval that excludes both endpoints a and b (is open on both the left and the right).

The function returns a new Polars `Series` where each value is replaced by the interval it matches.
