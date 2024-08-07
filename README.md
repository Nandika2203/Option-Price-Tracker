# Option-Price-Tracker

This project involves calculating the number of minutes between two datetime values and determining the percentile of option prices based on certain criteria.

## Project Overview

The main functionalities of this project include:
1. Loading a dataset from a CSV file.
2. Filtering data based on an index and date criteria.
3. Calculating the number of minutes between two datetime values.
4. Computing the percentile of option prices (CE, PE, Total) based on DTE (Days to Expiry) and the given value.

## Requirements

To run this project, you need to have the following Python packages installed:

- pandas
- scipy

You can install these dependencies using the `requirements.txt` file provided.

## Usage

1. Load the dataset by providing the correct file path.
2. Use the provided functions to filter the dataset and calculate the required values.

### Example

```python
filepath = "oldexpiries.csv"
dataset = pd.read_csv(filepath)

input_date = "2023-08-07"
time_str = "12:00:00"
index = "NIFTY"

next_date = get_next_date_from_csv(filepath, input_date, index)

if next_date is not None:
    date_value = next_date.date()
    DTE = calculate_DTE(input_date, time_str, date_value)
    print(f"The expiry date for index {index} is: {date_value}")
    print(f"The DTE value: {DTE}")
    
    option_type1 = "CE"
    option_value1 = 50.0
    calculate_percentile(DTE, option_value1, option_type1)
else:
    print("No next date found.")
