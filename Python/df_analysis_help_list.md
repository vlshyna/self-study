#### Creating functions for future custom library

```python
import pandas as pd
from pathlib impoer Path
from IPython.display import display

def read_csv_preview(file_path: str | Path, n_rows: int = 5) -> pd.DataFrame:
  """
  Reads a csv file and displays a quick overview of the dataset:
      1) first n_rows of the dataset
      2) column names, data types, non-null value count
      3) descriptive statistics for num columns

  Params
  # ---------------------------------------------------------
  1) file_path: str | Path
        path to the csv file
  2) n_rows: int, def value = 5
        num of rows to display

  Returns
  # ---------------------------------------------------------
  pd.DataFrame
      loaded dataset
  """

  if n_rows < 0:
      raise ValueError("n_rows must be greater than 0")

  file_path = Path(file_path)
  df = pd.read_csv(file_path)

  # ---------------------------------------------------------
  # Dataset overview
  # ---------------------------------------------------------
  n_rows, n_columns = df.shape

  print(
          f"Dataset contains {n_rows:,} rows "
          f"and {n_columns:,} variables."
      )
  print("Quick preview")
  print("-" * 40)
  display(df.head(n_rows))

  print("\nColumns Info")
  print("-" * 40)
  df.info()

  print("\nDescriptive Statistics")
  print("-" * 40)
  display(df.describe())

  return df
```
