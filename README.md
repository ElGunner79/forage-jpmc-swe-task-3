# JPMC Task 3

# Stock Ratio Visualization App

## Overview
This app is designed to provide traders with a visual representation of the ratio between two stocks over time. It also tracks and displays the historical correlation of these ratios with defined upper and lower bounds, helping traders identify potential trading opportunities.

## Features
- Real-time data streaming of stock prices
- Visualization of the ratio between two selected stocks
- Display of historical correlation with upper and lower bounds
- Alerts when the ratio crosses defined thresholds

## Installation
1. Clone the repository:
    ```bash
    git clone https://github.com/your-repo/stock-ratio-visualization.git
    ```
2. Navigate to the project directory:
    ```bash
    cd stock-ratio-visualization
    ```
3. Install the dependencies:
    ```bash
    npm install
    ```

## Usage
1. Start the development server:
    ```bash
    npm start
    ```
2. Open your browser and go to `http://localhost:3000`.

## Implementation Details

### Objective 1: Track the Ratio of Two Stocks
To make the graph more useful for traders, we track the ratio between two stocks over time instead of their individual top ask prices.

### Objective 2: Historical Correlation and Alerts
We plot the historical correlation with upper and lower bounds and show when these bounds are crossed to help traders determine trading opportunities.

### Steps to Achieve the Objectives

#### Graph Component (`Graph.tsx`)
1. **Modify `componentDidMount` Method:**
    - Update the schema object to configure the Perspective table view of the graph.
    - Add fields: `ratio`, `upper_bound`, `lower_bound`, and `trigger_alert`.
    - Add `price_abc` and `price_def` to calculate the ratio but do not configure the graph to show them.
    - Include a `timestamp` field for tracking data over time.

2. **Update Graph Attributes:**
    - Change `view` to `y_line`.
    - Remove `column-pivots` since we focus on ratios rather than individual stock prices.
    - Set `row-pivots` to map each data point based on its timestamp.
    - Focus `columns` on `ratio`, `lower_bound`, `upper_bound`, and `trigger_alert`.
    - Handle duplicate data using `aggregates`.

3. **Modify `componentDidUpdate` Method:**
    - Update the argument passed to `this.table.update` to ensure consistency with the new schema.

#### Data Manipulation (`DataManipulator.ts`)
1. **Update Row Interface:**
    - Modify the Row interface to match the new schema in `Graph.tsx`.

2. **Update `generateRow` Function:**
    - Compute `price_abc` and `price_def`.
    - Calculate the `ratio` using both prices.
    - Set `lower_bound` and `upper_bound`.
    - Determine `trigger_alert`.

## Additional Resources
- [React State and Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)
- [TypeScript Interfaces](https://www.typescriptlang.org/docs/handbook/interfaces.html)
- [Perspective Documentation](https://github.com/finos/perspective/tree/master/packages/perspective#tableupdatedata)

## Contributing
Contributions are welcome! Please open an issue or submit a pull request for any improvements.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

