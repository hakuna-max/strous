# 项目设置指南

当使用 Visual Studio 管理多个项目时，为了避免编译过程中的文件冲突，建议为每个项目单独设置输出目录（Output Directory）和中间目录（Intermediate Directory）。以下是设置步骤：

## 设置 Output Directory

为了将每个项目的编译输出文件存放在单独的目录中，请按照以下步骤设置 Output Directory：

1. 右键点击解决方案资源管理器中的项目，选择 "属性"。
2. 在属性页面中，导航到 "配置属性" > "常规"。
3. 在 "输出目录" 选项中，设置以下路径：

   ```
   $(SolutionDir)bin\$(ProjectName)\$(Platform)\$(Configuration)\
   ```

   这样设置后，输出文件将被存放在 `bin` 目录下，按照项目名称、平台和配置进行分类。

## 设置 Intermediate Directory

为了避免中间文件之间的冲突，每个项目也应有其独立的中间目录。请按照以下步骤设置 Intermediate Directory：

1. 同样在项目的属性页面中，导航到 "配置属性" > "常规"。
2. 在 "中间目录" 选项中，设置以下路径：

   ```
   $(SolutionDir)bin\intermediates\$(ProjectName)\$(Platform)\$(Configuration)\
   ```

   修改后，中间文件（如 `.obj` 文件）将存放在以项目名称命名的子文件夹中，避免了不同项目之间的文件冲突。

请确保在解决方案中的每个项目上都应用以上设置，以保持一致性和避免潜在的构建问题。