# Git 操作 (70-72)

> ⭐⭐ 中等 | 分类：版本控制 | 预估时间：3 分钟

### 场景描述

在 Vim 中直接操作 Git，提高开发效率。

---

## 70. 查看当前行 Git blame

> 难度：⭐⭐ | 预估时间：1 分钟

### 初始状态

```python
def hello():  # 光标在这里
    pass
```

---

### 操作方法

**方法一：Gitsigns（推荐）**

```vim
:Gitsigns blame_line
```

**方法二：Telescope**

```vim
<leader>gb
```

---

### 关键命令解析

| 命令                   | 作用            |
| ---------------------- | --------------- |
| `:Gitsigns blame_line` | blame 当前行    |
| `<leader>gb`           | Telescope blame |

---

### 检验清单

- [ ] 能查看行级别的 blame
- [ ] 知道如何查看完整 blame

---

## 71. 查看文件 Git diff

> 难度：⭐⭐ | 预估时间：1 分钟

### 初始状态

```python
def hello():
    print("old")
```

---

### 操作方法

**方法一：Gitsigns**

```vim
:Gitsigns diffthis
```

**方法二：Fugitive**

```vim
:Gvdiff
```

**方法三：命令行**

```vim
:Git diff
```

---

### 关键命令解析

| 命令                 | 作用          |
| -------------------- | ------------- |
| `:Gitsigns diffthis` | 显示差异      |
| `:Gvdiff`            | 垂直分屏 diff |
| `:Git diff`          | 命令行 diff   |

---

### 检验清单

- [ ] 能查看当前文件差异
- [ ] 知道分屏 diff 的方法

---

## 72. 跳转到冲突位置

> 难度：⭐⭐ | 预估时间：1 分钟

### 初始状态

```python
<<<<<<< HEAD
version_a = 1
=======
version_b = 2
>>>>>>> branch
```

---

### 操作方法

**方法一：Telescope（推荐）**

```vim
<leader>gc
```

**方法二：gitconflict 插件**

```vim
:GitConflictList
```

**方法三：手动跳转**

```vim
<<<<<<<
```

---

### 操作冲突

| 命令                         | 作用     |
| ---------------------------- | -------- |
| `:GitConflictChooseCurrent`  | 保留当前 |
| `:GitConflictChooseIncoming` | 保留传入 |
| `:GitConflictChooseBoth`     | 保留两者 |

---

### 检验清单

- [ ] 能快速定位冲突
- [ ] 知道如何解决冲突

---

## Git 操作速查

| 操作      | 命令                   | 说明           |
| --------- | ---------------------- | -------------- |
| blame     | `:Gitsigns blame_line` | 查看行修改信息 |
| diff      | `:Gitsigns diffthis`   | 查看差异       |
| 跳转冲突  | `:cn`                  | 下一个冲突     |
| 解决冲突  | `:GitConflictChooseX`  | 选择版本       |
| status    | `:Gitsigns status`     | 查看状态       |
| Telescope | `<leader>gc`           | 冲突列表       |

---

### 视频时间点

- **0:00** - 题目介绍
- **0:30** - 演示第 70 题
- **1:15** - 演示第 71 题
- **1:45** - 演示第 72 题
- **2:30** - 速查表

---

> **提示**：LazyVim 预置了 gitsigns 和 fugitive。
