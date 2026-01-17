# LSP 和智能代码操作

## 152. 代码补全和建议

**场景**：使用 LSP 提供的智能补全

**示例：函数参数补全**

**初始**：

```javascript
function calculateTotal(price, quantity, taxRate) {
  return price * quantity * (1 + taxRate);
}

// 调用时
calculateTotal(|)  ← 光标位置
```

**操作**：

1. 开始输入参数
2. `Ctrl-Space` 触发补全
3. LSP 会显示参数提示
4. `Tab` 或 `Enter` 选择建议

**补全类型**：

- 变量名补全
- 函数名补全
- 方法补全
- 属性补全
- 导入建议
- 代码片段

**快捷键（LazyVim）**：

- `Ctrl-Space` - 触发补全
- `Ctrl-n` / `Ctrl-p` - 上下选择
- `Ctrl-y` - 确认选择
- `Ctrl-e` - 取消补全

## 153. 跳转到定义和引用

**场景**：快速导航代码

**示例代码**：

```javascript
// utils.js
export function formatDate(date) {
  return date.toLocaleDateString();
}

// app.js
import { formatDate } from "./utils";

const today = formatDate(new Date()); // 光标在 formatDate 上
```

**操作**：

- `gd` - 跳转到定义（Go to Definition）
- `gD` - 跳转到声明
- `gr` - 查找引用（Go to References）
- `gi` - 跳转到实现
- `gy` - 跳转到类型定义
- `Ctrl-o` - 跳回上一个位置
- `Ctrl-i` - 跳到下一个位置

**LazyVim 快捷键**：

- `<leader>cr` - 查看引用
- `K` - 显示悬浮文档
- `gK` - 显示签名帮助

## 154. 代码重命名

**场景**：重命名变量、函数、类等符号

**初始**：

```javascript
function oldFunctionName(param) {
  const oldVar = param * 2;
  return oldVar;
}

const result1 = oldFunctionName(10);
const result2 = oldFunctionName(20);
```

**操作**：

1. 将光标放在 `oldFunctionName` 上
2. `<leader>cr` 或 `:lua vim.lsp.buf.rename()`
3. 输入新名称 `newFunctionName`
4. Enter 确认

**目标**：

```javascript
function newFunctionName(param) {
  const oldVar = param * 2;
  return oldVar;
}

const result1 = newFunctionName(10);
const result2 = newFunctionName(20);
```

**重命名影响**：

- 当前文件的所有引用
- 其他文件的所有引用
- 自动更新导入语句

## 155. 代码诊断和错误修复

**场景**：查看和修复代码错误

**示例：未使用的导入**

**初始**：

```javascript
import React, { useState, useEffect } from "react"; // useEffect 未使用

function App() {
  const [count, setCount] = useState(0);
  return <div>{count}</div>;
}
```

**诊断信息**：

```text
'useEffect' is defined but never used
```

**操作**：

- `]d` - 下一个诊断
- `[d` - 上一个诊断
- `<leader>cd` - 查看诊断列表
- `<leader>ca` - 代码操作（Code Action）
- 在错误处按 `<leader>ca` 选择 "Remove unused import"

**目标**：

```javascript
import React, { useState } from "react";

function App() {
  const [count, setCount] = useState(0);
  return <div>{count}</div>;
}
```

## 156. 自动导入

**场景**：自动添加缺失的导入

**初始**：

```javascript
// 使用了 useState 但未导入
function Counter() {
  const [count, setCount] = useState(0); // ← 错误：useState 未定义
  return <div>{count}</div>;
}
```

**操作**：

1. 光标移到 `useState`
2. `<leader>ca` 打开代码操作
3. 选择 "Add import from 'react'"

**目标**：

```javascript
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);
  return <div>{count}</div>;
}
```

## 157. 代码格式化

**场景**：自动格式化代码

**初始**：

```javascript
function messy(a, b, c) {
  const x = a + b;
  const y = x * c;
  return y;
}
```

**操作**：

- `<leader>cf` - 格式化当前文件
- 或 `:lua vim.lsp.buf.format()`
- 保存时自动格式化（如果配置了）

**目标**：

```javascript
function messy(a, b, c) {
  const x = a + b;
  const y = x * c;
  return y;
}
```

**格式化选项**：

- 格式化整个文件
- 格式化选中区域：选中后 `<leader>cf`
- 配置格式化工具（Prettier, ESLint 等）

## 158. 代码折叠和展开

**场景**：使用 LSP 提供的智能折叠

**示例代码**：

```javascript
class UserService {
  constructor() {
    this.users = [];
  }

  async getUser(id) {
    const response = await fetch(`/api/users/${id}`);
    return await response.json();
  }

  async createUser(userData) {
    const response = await fetch("/api/users", {
      method: "POST",
      body: JSON.stringify(userData),
    });
    return await response.json();
  }
}
```

**操作**：

- `za` - 切换折叠
- `zc` - 关闭折叠
- `zo` - 打开折叠
- `zR` - 打开所有折叠
- `zM` - 关闭所有折叠
- `zj` - 移到下一个折叠
- `zk` - 移到上一个折叠

**折叠后**：

```javascript
class UserService {
  constructor() {...}
  async getUser(id) {...}
  async createUser(userData) {...}
}
```

## 159. 函数签名帮助

**场景**：查看函数参数提示

**示例**：

```javascript
// 编写代码时
Math.max(|)  ← 光标位置，需要知道参数
```

**操作**：

- `Ctrl-k` - 显示签名帮助（在插入模式）
- `K` - 显示悬浮文档（在普通模式）

**显示**：

```text
Math.max(value1: number, value2: number, ...values: number[]): number

返回提供的数字表达式中较大的一个
```

## 160. 代码操作和快速修复

**场景**：使用 LSP 提供的代码操作

**示例 1：提取变量**

**初始**：

```javascript
function calculate() {
  return (price * 1.2 + 10) * 0.9;
}
```

**操作**：

1. 选中 `price * 1.2 + 10`
2. `<leader>ca` 代码操作
3. 选择 "Extract to constant"

**目标**：

```javascript
function calculate() {
  const tempPrice = price * 1.2 + 10;
  return tempPrice * 0.9;
}
```

**示例 2：实现接口**

**初始**：

```typescript
interface Animal {
  name: string;
  makeSound(): void;
}

class Dog implements Animal {
  // ← 错误：未实现接口
}
```

**操作**：

1. 光标在 `Dog` 上
2. `<leader>ca`
3. 选择 "Implement interface Animal"

**目标**：

```typescript
class Dog implements Animal {
  name: string;

  makeSound(): void {
    throw new Error("Method not implemented.");
  }
}
```

## 161. 符号搜索

**场景**：在项目中搜索符号

**任务**：查找所有名为 `User` 的类、接口或类型

**操作**：

- `<leader>ss` - 搜索文档符号
- `<leader>sS` - 搜索工作区符号
- 输入 `User` 查找

**显示结果**：

```text
□ class User (models/User.ts)
□ interface User (types/User.ts)
□ type UserResponse (api/types.ts)
```

**符号类型**：

- 类 (Class)
- 接口 (Interface)
- 函数 (Function)
- 变量 (Variable)
- 常量 (Constant)
- 枚举 (Enum)

## 162. 代码大纲和结构

**场景**：查看文件的代码结构

**示例文件**：

```javascript
class TodoList {
  constructor() {}
  addTodo(text) {}
  removeTodo(id) {}
  getTodos() {}
}

function saveTodos() {}
function loadTodos() {}

const API_URL = "https://api.example.com";
```

**操作**：

- `<leader>cs` - 查看符号大纲（Document Symbols）
- 或使用侧边栏的大纲视图

**显示**：

```text
📦 TodoList (class)
  ├─ constructor
  ├─ addTodo
  ├─ removeTodo
  └─ getTodos
⚡ saveTodos (function)
⚡ loadTodos (function)
🔢 API_URL (constant)
```

## 163. 内联提示

**场景**：显示类型提示和参数名称

**示例**：

```typescript
// 启用内联提示后
function greet(name: string, age: number) {
  console.log(`Hello ${name}, you are ${age}`);
}

greet("John", 30);
// 显示为：
// greet(name: "John", age: 30);
//        ^^^^        ^^^^  ← 参数名称提示
```

**配置**：

```lua
vim.lsp.inlay_hint.enable(true)
```

**切换**：

- `<leader>uh` - 切换内联提示（LazyVim）

## 164. 调用层次结构

**场景**：查看函数的调用关系

**示例**：

```javascript
function processData() {
  validateData();
  transformData();
  saveData();
}

function validateData() {}
function transformData() {}
function saveData() {}
```

**操作**：

1. 光标在 `processData` 上
2. `<leader>ci` - 显示传入调用（谁调用了这个函数）
3. `<leader>co` - 显示传出调用（这个函数调用了谁）

**显示**：

```text
processData 调用：
  ├─ validateData
  ├─ transformData
  └─ saveData
```

## 165. LSP 工作区管理

**场景**：管理多个项目文件夹

**任务**：

1. 添加工作区文件夹
2. 移除工作区文件夹
3. 列出工作区文件夹

**操作**：

```vim
:lua vim.lsp.buf.add_workspace_folder()
:lua vim.lsp.buf.remove_workspace_folder()
:lua print(vim.inspect(vim.lsp.buf.list_workspace_folders()))
```

**使用场景**：

- Monorepo 项目
- 多个相关项目
- 共享库引用
