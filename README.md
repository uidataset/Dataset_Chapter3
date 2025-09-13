# 第三章中的数据集

该数据集包含 2,500 个文本提示，涵盖 10 个应用领域的 100 项任务，总共包含 533 条原始指令（original instructions）和 543 条实际操作指令（actual instructions）。每项任务都对应一个教程。

## 数据集结构

根目录包含以下内容：

- `Tutorial/` - 一个目录，其中包含每个具体教程的子目录。
- `textual_prompts.xlsx` - 一个 Excel 文件，包含 100 个不同任务的 2,500 个文本提示。

### Tutorial 目录

数据集中的每个目录都以其包含的教程名称命名。每个目录包含以下文件：

- `tutorial.json`：一个 JSON 文件，包含教程的元数据。
- 每条指令对应的无障碍节点树，以及该指令的屏幕截图。

请注意，有 **2 个教程无法使用无障碍服务（Accessibility Service）API 完成**，它们是 `在华为手机中开启手写功能的步骤` 和 `在手机QQ中进入自习室的步骤`。因此，这两个教程的 `tutorial.json` 文件中没有 `actual_instructions` 字段。

#### tutorial.json 文件说明

`tutorial.json` 文件包含以下字段：

- `tutorialName`: 教程的名称。
- `tutorialDetail`: 教程的详细信息，可视为原始文本。
- `original_instructions`: 原始指令，是解析代理（Parsing Agent）将教程详情作为输入后产生的结果。
- `actual_instructions`: 实际操作指令，是定位代理（Grounding Agent）产生的结果。每条指令包含以下字段：
  - `targetName`: 目标节点的名称。
  - `type`: 指令的类型。
  - `para`: 指令的参数。
  - `x`: 目标节点的 x 坐标。
  - `y`: 目标节点的 y 坐标。
  - `endX`: 指令结束点的 x 坐标（仅用于滚动指令）。
  - `endY`: 指令结束点的 y 坐标（仅用于滚动指令）。
  - `storeFolder`: 存储该指令对应的无障碍节点树的文件夹名称。该文件夹与 `tutorial.json` 文件位于同一目录下，其中的无障碍节点树存储在名为 `target_node.json` 的文件中。
  - `absoluteId`: 目标节点在无障碍节点树中的绝对 ID。
  - `description`: 指令的描述。
  - `imagePath`: 该指令的屏幕截图路径。该截图与 `tutorial.json` 文件位于同一目录下，并存储在名为 `[imagePath]` + `.jpg` 的文件中。

## 备注信息

数据是在具有以下规格的安卓手机上收集的：

- **型号**: 荣耀 V20 (HONOR V20)
- **Android 版本**: 33
- **屏幕分辨率**: 2310 x 1080 像素
