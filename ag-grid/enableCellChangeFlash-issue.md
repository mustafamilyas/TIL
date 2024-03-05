# enableCellChangeFlash Issue

## Problem

When using `enableCellChangeFlash`, it will flash the cell when the cell value is changed. However sometimes it doesn't work as expected, it will only flash very briefly or not at all.

## Root Cause

1. The cell value is not changed. You should check the cell value and make sure it's changed.
2. The cell value is changed but the grid doesn't know about it. You should check the connection between the grid and the data source.
3. The cell value is changed and flash briefly. If you have a dynamic row class, it will rerender the row and the flash will be gone. Try to remove the dynamic row class and see if it works.
