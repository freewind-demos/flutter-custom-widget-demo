# Flutter 自定义 Widget（组合 ElevatedButton）

## 简介

抽取 **`MyButton`**（`StatelessWidget`），对外暴露 `text` 与 `onPressed`，内部拼出 `ElevatedButton`。演示「如何用组合而不是继承」复用一块 UI。

## 快速开始

### 环境要求

Flutter SDK。

### 运行

```bash
flutter pub get
flutter run
```

## 概念讲解

### 第一部分：构造函数用 `required` 命名参数

`const MyButton({required this.text, required this.onPressed})` 让调用方必须传文案与回调，减少空回调遗漏。

### 第二部分：何时拆 Widget

当同一段结构在 2～3 处出现、或单文件 `build` 过长时，应拆子 Widget。过小 prematurely 抽象也会增加跳转成本。

## 完整示例

`lib/main.dart`：`MyApp` 中央调用 `MyButton(text: 'Click Me', onPressed: () => print('Clicked!'))`。

## 注意事项

- 生产代码应用日志或调试工具替代裸 `print`。
- 若子部件需复用样式令牌，考虑 `Theme` 或 `ButtonStyle`。

## 完整讲解（中文）

Flutter 鼓励 **组合优于继承**：你不一定要 `extends ElevatedButton`，而是 **持有一个** `ElevatedButton` 并往里塞参数。`MyButton` 这种薄封装最适合统一全站主按钮样式：以后要改成 `FilledButton` 或加图标，只改这一处。
