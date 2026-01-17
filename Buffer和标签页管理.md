# Buffer 和标签页管理

## 102. 在多个 Buffer 之间快速切换

**场景**：你正在编辑多个文件，需要快速在它们之间切换

**初始状态**：

- 当前有 3 个打开的 buffer：
  - buffer 1: `app.js`
  - buffer 2: `utils.js` (当前)
  - buffer 3: `config.js`

**目标**：

1. 切换到上一个 buffer (app.js)
2. 切换到下一个 buffer (config.js)
3. 跳转到指定 buffer (buffer 1)
4. 列出所有 buffer

**操作提示**：

- `:bp` 或 `:bprevious` - 上一个 buffer
- `:bn` 或 `:bnext` - 下一个 buffer
- `:b1` 或 `:buffer 1` - 跳转到 buffer 1
- `:ls` 或 `:buffers` - 列出所有 buffer
- `Ctrl-6` 或 `Ctrl-^` - 在当前和上一个 buffer 间切换

## 103. 关闭和删除 Buffer

**场景**：清理不再需要的 buffer

**初始状态**：

```text
当前打开的 buffers:
1. README.md
2. main.js (当前，已修改)
3. test.js (未保存的更改)
4. temp.txt (临时文件，不需要)
```

**目标**：

1. 关闭当前 buffer 但保留窗口
2. 删除指定的 buffer (temp.txt)
3. 关闭所有未修改的 buffer
4. 强制关闭包含未保存更改的 buffer

**操作提示**：

- `:bd` 或 `:bdelete` - 删除当前 buffer
- `:bd 4` - 删除 buffer 4
- `:bd temp.txt` - 根据名称删除
- `:bd!` - 强制删除（丢弃更改）
- `:%bd` - 删除所有 buffer
- `:%bd|e#|bd#` - 只保留当前 buffer

## 104. 标签页管理

**场景**：使用标签页组织不同的工作区

**任务**：

1. 新建一个标签页
2. 在新标签页中打开文件
3. 在标签页之间切换
4. 移动标签页位置
5. 关闭标签页

**操作提示**：

- `:tabnew` - 新建标签页
- `:tabnew file.js` - 在新标签页打开文件
- `gt` - 下一个标签页
- `gT` - 上一个标签页
- `2gt` - 跳转到第 2 个标签页
- `:tabmove 0` - 移动到第一个位置
- `:tabc` 或 `:tabclose` - 关闭当前标签页
- `:tabo` 或 `:tabonly` - 只保留当前标签页

## 105. Buffer 重命名和保存

**场景**：重命名 buffer 或另存为新文件

**初始状态**：

```text
当前文件: draft.txt
内容:
This is my draft content.
Need to save it with a better name.
```

**目标**：

1. 将当前文件另存为 `final.txt`
2. 保存所有打开的 buffer
3. 只读模式打开后需要强制保存

**操作提示**：

- `:w new_name.txt` - 另存为（原文件仍在 buffer 中）
- `:saveas new_name.txt` - 另存为并切换到新文件
- `:file new_name.txt` - 重命名 buffer（不保存）
- `:wa` 或 `:wall` - 保存所有 buffer
- `:w!` - 强制保存（覆盖只读）
- `:up` - 仅在有修改时保存

## 106. 分割窗口中的 Buffer 操作

**场景**：在分割窗口中管理 buffer

**任务**：

1. 在新的水平分割中打开 buffer
2. 在新的垂直分割中打开 buffer
3. 在所有窗口中打开不同的 buffer
4. 关闭窗口但保留 buffer

**操作提示**：

- `:sb 2` - 在水平分割中打开 buffer 2
- `:vert sb 3` - 在垂直分割中打开 buffer 3
- `:ba` 或 `:ball` - 在多个窗口中打开所有 buffer
- `Ctrl-w c` - 关闭窗口（buffer 保留）
- `Ctrl-w o` - 只保留当前窗口

## 107. Buffer 列表过滤和查找

**场景**：快速找到需要的 buffer

**初始状态**：

```text
打开了 20+ 个文件，需要找到：
- 所有 .js 文件
- 包含 "test" 的文件
- 最近修改的文件
```

**目标**：

1. 列出所有 buffer 并查找特定文件
2. 根据文件名模式切换 buffer
3. 跳转到包含特定内容的 buffer

**操作提示**：

- `:ls` - 列出所有 buffer
- `:b test` + `Tab` - 补全匹配 "test" 的 buffer
- `:b *.js` + `Tab` - 匹配所有 .js 文件
- `:bufdo` - 在所有 buffer 中执行命令
- `:bufdo %s/old/new/g` - 在所有 buffer 中替换

## 108. 隐藏和未列出的 Buffer

**场景**：理解 buffer 的不同状态

**Buffer 状态说明**：

```text
%  - 当前窗口的 buffer
#  - 轮换 buffer (Ctrl-^ 切换到的)
a  - 激活的 buffer (已加载且显示)
h  - 隐藏的 buffer (已加载但未显示)
u  - 未列出的 buffer
+  - 已修改的 buffer
=  - 只读 buffer
```

**任务**：

1. 查看所有 buffer 包括未列出的
2. 切换到隐藏的 buffer
3. 删除未列出的 buffer

**操作提示**：

- `:ls!` - 显示所有 buffer（包括未列出的）
- `:set hidden` - 允许切换未保存的 buffer
- `:unhide` - 打开所有隐藏的 buffer

## 109. 会话管理

**场景**：保存和恢复工作环境

**任务**：

1. 保存当前的所有 buffer、窗口布局、标签页
2. 下次启动时恢复会话
3. 管理多个会话（项目 A、项目 B）

**操作提示**：

- `:mksession session.vim` - 保存会话
- `:mksession! session.vim` - 覆盖保存
- `nvim -S session.vim` - 启动时加载会话
- `:source session.vim` - 在运行时加载会话
- `:mks! ~/sessions/project-a.vim` - 保存到指定位置

**会话包含的信息**：

- 所有打开的文件（buffers）
- 窗口布局
- 标签页
- 当前目录
- 全局标记
- 折叠状态

## 110. Buffer 批量操作

**场景**：对多个 buffer 执行相同操作

**示例任务**：

**任务 1：在所有 .js 文件中添加版权声明**

```javascript
// 需要在每个 .js buffer 的开头添加：
/*
 * Copyright 2024
 * Licensed under MIT
 */
```

**任务 2：在所有 buffer 中统一替换变量名**

```text
将所有文件中的 oldVarName 替换为 newVarName
```

**操作提示**：

- `:bufdo` - 对所有 buffer 执行命令
- `:bufdo %s/old/new/ge | update` - 替换并保存
- `:bufdo normal ggO// New line` - 在开头插入行
- `:argdo` - 对参数列表中的文件执行
- `:tabdo` - 对所有标签页执行
- `:windo` - 对所有窗口执行

**实用示例**：

```vim
" 在所有 buffer 中删除行尾空格并保存
:bufdo %s/\s\+$//e | update

" 在所有 .md 文件中添加 YAML front matter
:bufdo if expand('%:e') == 'md' | call append(0, ['---', 'title: ', '---', '']) | endif

" 保存所有已修改的 buffer
:bufdo if &modified | write | endif
```
