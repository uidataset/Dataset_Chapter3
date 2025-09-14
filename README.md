# 第三章中的数据集

该数据集包含 2,500 个文本输入，涵盖 10 个应用的 100 个任务，总共包含 533 条指令和 543 条实际操作。

## 数据集结构

根目录包含以下内容：

- `Tutorial/` - 包含每个具体任务的信息。
- `textual_prompts.xlsx` - 一个 Excel 文件，包含 100 个不同任务的 2,500 个文本输入。

### Tutorial 目录

数据集中的每个目录都以该任务的功能描述命名。每个目录包含以下文件：

- `tutorial.json`：一个 JSON 文件，包含该任务的元数据。
- 每条操作对应的布局树和屏幕截图。

请注意，有 **2 个任务无法使用无障碍服务 API 完成**，分别是 `在华为手机中开启手写功能的步骤` 和 `在手机QQ中进入自习室的步骤`。因此，这两个任务的 `tutorial.json` 文件中没有 `actual_instructions` 字段。

#### tutorial.json 文件说明

`tutorial.json` 文件包含以下字段：

- `tutorialName`: 任务的功能描述。
- `tutorialDetail`: 任务的步骤描述。
- `original_instructions`: 任务的指令列表。
- `actual_instructions`: 任务的操作序列。每个操作包含以下字段：
  - `targetName`: 目标控件的名称。
  - `type`: 操作的类型。
  - `para`: 操作的参数。
  - `x`: 目标控件的 x 坐标。
  - `y`: 目标控件的 y 坐标。
  - `endX`: 操作结束点的 x 坐标（仅用于滚动指令）。
  - `endY`: 操作结束点的 y 坐标（仅用于滚动指令）。
  - `storeFolder`: 存储该操作对应的布局树的文件夹名称。该文件夹与 `tutorial.json` 文件位于同一目录下，其中的布局树存储在名为 `target_node.json` 的文件中。
  - `absoluteId`: 目标控件在布局树中的ID。
  - `description`: 操作的描述。
  - `imagePath`: 操作对应的屏幕截图路径。该截图与 `tutorial.json` 文件位于同一目录下，并存储在名为 `[imagePath]` + `.jpg` 的文件中。

## 备注信息

数据是在以下规格的安卓手机上收集的：

- **型号**: 荣耀 V20
- **Android 版本**: 33
- **屏幕分辨率**: 2310 x 1080 像素
