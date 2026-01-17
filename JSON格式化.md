# JSON 格式化 (35-37)

> ⭐ 简单 | 数据处理

## 35. JSON 压缩格式化

**初始状态**：

```json
{
  "name": "John",
  "age": 30,
  "city": "New York"
}
```

**操作提示**：

```vim
" 使用外部命令压缩
:%!jq -c .

" 或 python
:%!python -m json.tool --compact
```

**目标状态**：

```json
{ "name": "John", "age": 30, "city": "New York" }
```

---

## 36. JSON 美化格式化

**初始状态**：

```json
{ "name": "John", "age": 30, "city": "New York" }
```

**操作提示**：

```vim
" 使用 jq 美化
:%!jq .

" 或 python
:%!python -m json.tool
```

**目标状态**：

```json
{
  "name": "John",
  "age": 30,
  "city": "New York"
}
```

---

## 37. 修复 JSON 逗号

**初始状态**：

```json
{
  "name": "John"
  "age": 30
  "city": "New York"
}
```

**操作提示**：

```vim
" 使用 substitute
:%s/"$/",/

" 或使用插件
" neogenia-jp/issue-keyword-matcher.vim
```

**目标状态**：

```json
{
  "name": "John",
  "age": 30,
  "city": "New York"
}
```

---

## JSON 命令速查

| 操作   | 命令                     | 说明          |
| ------ | ------------------------ | ------------- |
| 美化   | `:%!jq .`                | 格式化 JSON   |
| 压缩   | `:%!jq -c .`             | 压缩 JSON     |
| Python | `:%!python -m json.tool` | Python 格式化 |
