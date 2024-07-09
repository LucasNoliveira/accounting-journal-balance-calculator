# Accounting Journal Balance Calculator

This project helps accountants get balances from accounting journals based on specific user inputs. It includes a form for inputting accounts, journal entries, and user parameters, as well as a display component to show the calculated balances.

## Components

### InputForm Component

The `InputForm` component allows the user to input account data, journal entries, and user-specific parameters. The state is managed within the component and the data is dispatched to the Redux store upon form submission.

#### Key Features:
- Captures user input for accounts, journal entries, and parameters.
- Dispatches actions to set accounts, journal entries, and user input in the Redux store.
- Automatically submits the form on component mount for initial data processing.

### BalanceOutput Component

The `BalanceOutput` component displays the calculated balance data based on the user input. It filters and processes the journal entries and accounts to calculate the debit, credit, and balance for each account.

#### Key Features:
- Connects to the Redux store to access user input, journal entries, and accounts.
- Filters journal entries based on account range and period specified by the user.
- Groups entries by account and calculates the total debit, credit, and balance.
- Displays the results in either HTML table or CSV format, based on user preference.

## Redux Integration

### Actions

Three actions are defined to manage the state of accounts, journal entries, and user input:
- `SET_ACCOUNTS`: Sets the account data.
- `SET_JOURNAL_ENTRIES`: Sets the journal entries.
- `SET_USER_INPUT`: Sets the user input parameters.

### Reducers

A reducer for `userInput` is implemented to handle the `SET_USER_INPUT` action and update the state with the user-provided parameters.

### Utilities

Helper functions are provided to parse CSV data, convert dates, and process user input strings:
- `parseCSV`: Parses CSV strings into objects.
- `stringToDate` and `dateToString`: Convert date strings to Date objects and vice versa.
- `parseUserInput`: Parses the user input string into an object with specific parameters.

## Implementation Details

### Filtering and Calculating Balance

The main logic for filtering journal entries and calculating balances is implemented in the `mapStateToProps` function of the `BalanceOutput` component:

1. **Extract User Input**: Extracts the account range and period range from the user input stored in the Redux state.

2. **Filter Journal Entries**: Filters the journal entries based on the specified account range and period range.

3. **Group by Account**: Groups the filtered entries by account number and sums the debit and credit amounts for each account.

4. **Calculate Balance**: Calculates the balance for each account as the difference between total debit and credit.

5. **Calculate Totals**: Calculates the total debit and total credit across all accounts.

This logic ensures that the balance data is accurately calculated and formatted based on the user's specifications.

## Usage

1. **Input Data**: Enter account data, journal entries, and user parameters in the form.
2. **Submit Form**: The form is automatically submitted on component mount, or can be manually submitted to process the data.
3. **View Results**: The calculated balances are displayed in the desired format (HTML table or CSV) based on the user input.

## Example User Inputs

- `1000 5000 MAR-16 JUL-16 HTML`: Outputs all accounts from 1000 to 5000 for the period March 2016 to July 2016, formatted as an HTML table.
- `2000 * * MAY-16 CSV`: Outputs all accounts from 2000 onwards up to May 2016, formatted as CSV.

## Conclusion

This project demonstrates how to capture user input, process and filter data, and calculate and display results using React and Redux. The implementation provides a flexible and user-friendly way for accountants to obtain balance data from accounting journals.
