# Makes All Columns Take Full Width

When you have a large number of columns, it is not always possible to fit them all into the width of the grid. When this happens, the grid will display a horizontal scrollbar. This is fine, but sometimes you want to make the columns take up the full width of the grid, so user doesn't have to scroll to see all the columns.

You can achieve this by setting the `flex` property of the columns to `1`. This will make all the columns take up the full width of the grid.

```javascript
const columnDefs = [
  { field: "make", flex: 1 },
  { field: "model", flex: 1 },
  { field: "price", flex: 1 },
];
```

### Example

```javascript
import React from "react";

import { AgGridReact } from "ag-grid-react";
import "ag-grid-community/dist/styles/ag-grid.css";
import "ag-grid-community/dist/styles/ag-theme-alpine.css";

const App = () => {
  const rowData = [
    { make: "Toyota", model: "Celica", price: 35000 },
    { make: "Ford", model: "Mondeo", price: 32000 },
    { make: "Porsche", model: "Boxster", price: 72000 },
  ];

  const columnDefs = [
    { field: "make", flex: 1 },
    { field: "model", flex: 1 },
    { field: "price", flex: 1 },
  ];

  return (
    <div
      className="ag-theme-alpine"
      style={{
        height: "200px",
        width: "600px",
      }}
    >
      <AgGridReact columnDefs={columnDefs} rowData={rowData}></AgGridReact>
    </div>
  );
};

export default App;
```

### References

- [AG-Grid Documentation | flex properties](https://ag-grid.com/react-data-grid/column-properties/#reference-width-flex)
