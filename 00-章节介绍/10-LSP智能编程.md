# 第 10 章：LSP 智能编程

> 本章涵盖 152-165 题，学习 LSP 补全、跳转、重命名等功能。

## 核心技能

| 技能       | 命令         | 说明       |
| ---------- | ------------ | ---------- |
| 代码补全   | `Ctrl-n`     | 触发补全   |
| 跳转到定义 | `gd`         | LSP 跳转   |
| 查找引用   | `gr`         | 查找引用   |
| 重命名     | `<leader>cr` | 重命名符号 |

## 学习路径

```
第 1 周：代码补全 (152-155)
第 2 周：跳转导航 (156-158)
第 3 周：重构操作 (159-162)
第 4 周：诊断与修复 (163-165)
```

## 关键命令速查

```vim
" 代码补全
Ctrl-n       " 补全菜单
Ctrl-p       " 上一个候选
Ctrl-y       " 确认补全
Ctrl-e       " 取消补全

" LSP 导航
gd           " 跳转到定义
gr           " 查找引用
gi           " 跳转到上一次位置
gI           " 跳转到上一次修改

" 代码重构
<leader>cr   " 重命名
<leader>ca   " 代码操作
<leader>cf   " 格式化
<leader>cd   " 查看诊断

" 诊断跳转
]d           " 下一个错误
[d           " 上一个错误
:lua vim.diagnostic.goto_next()
:lua vim.diagnostic.goto_prev()
```

## 常见场景

1. **代码补全**：变量、函数、API
2. **重构变量**：批量重命名
3. **查看错误**：诊断信息
4. **代码修复**：快速修复建议

## LSP 服务器配置

```lua
-- Mason 安装 LSP
:Mason

-- 常用 LSP
lua_ls        " Lua
pyright       " Python
tsserver      " TypeScript
rust-analyzer " Rust
gopls         " Go
```

## 插件推荐

- **nvim-lspconfig**：LSP 配置
- **nvim-cmp**：补全引擎
- **friendly-snippets**：补全片段
- **trouble**：诊断列表

## 视频时间点

- **0:00** - 本章介绍
- **0:30** - 代码补全
- **1:00** - 跳转导航
- **1:30** - 代码重构
- **2:00** - 诊断修复
- **2:30** - 实战演练
