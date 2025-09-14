# Dataset in Chapter 3

This dataset includes 2,500 textual inputs, spanning 100 tasks across 10 applications, with a total of 533 instructions and 543 actual operations.

## Dataset Structure

The root directory contains the following:

-   `Tutorial/` - Contains information for each specific task.
-   `textual_prompts.xlsx` - An Excel file containing 2,500 textual inputs for 100 different tasks.

### Tutorial Directory

Each directory in the dataset is named after the functional description of the task. Each directory contains the following files:

-   `tutorial.json`: A JSON file containing the metadata for the task.
-   The layout tree and screenshot corresponding to each operation.

Please note that there are **2 tasks that cannot be completed using the Accessibility Service API**, which are `在华为手机中开启手写功能的步骤` and `在手机QQ中进入自习室的步骤`. Therefore, the `tutorial.json` files for these two tasks do not have the `actual_instructions` field.

#### `tutorial.json` File Description

The `tutorial.json` file contains the following fields:

-   `tutorialName`: The functional description of the task.
-   `tutorialDetail`: The step-by-step description of the task.
-   `original_instructions`: The list of instructions for the task.
-   `actual_instructions`: The sequence of operations for the task. Each operation contains the following fields:
    -   `targetName`: The name of the target widget.
    -   `type`: The type of the operation.
    -   `para`: The parameters of the operation.
    -   `x`: The x coordinate of the target widget.
    -   `y`: The y coordinate of the target widget.
    -   `endX`: The x coordinate of the operation's end point (only for scroll operations).
    -   `endY`: The y coordinate of the operation's end point (only for scroll operations).
    -   `storeFolder`: The name of the folder where the layout tree for this operation is stored. This folder is located in the same directory as the `tutorial.json` file, and the layout tree is stored in a file named `target_node.json`.
    -   `absoluteId`: The ID of the target widget in the layout tree.
    -   `description`: The description of the operation.
    -   `imagePath`: The path to the screenshot corresponding to the operation. The screenshot is located in the same directory as the `tutorial.json` file and is stored in a file named `[imagePath]` + `.jpg`.

## Additional Notes

The data was collected on an Android phone with the following specifications:

-   **Model**: HONOR V20
-   **Android version**: 33
-   **Screen resolution**: 2310 x 1080 pixels
