# URL 处理 (84-86)

> ⭐⭐ 中等 | Web 开发

## 84. 提取 URL 参数

**初始状态**：

```text
https://example.com?name=John&age=30&city=NYC
```

**操作提示**：

```vim
:!echo "https://example.com?name=John&age=30&city=NYC" | cut -d'?' -f2 | tr '&' '\n'
```

**目标状态**：

```text
name: John
age: 30
city: NYC
```

---

## 85. URL 编码

**初始状态**：

```text
hello world & special/chars
```

**操作提示**：

```vim
:!python -c "import urllib.parse; print(urllib.parse.quote('''hello world & special/chars'''))"
```

**目标状态**：

```text
hello%20world%20%26%20special%2Fchars
```

---

## 86. URL 解码

**初始状态**：

```text
hello%20world%20%26%20special%2Fchars
```

**操作提示**：

```vim
:!python -c "import urllib.parse; print(urllib.parse.unquote('hello%20world%20%26%20special%2Fchars'))"
```

**目标状态**：

```text
hello world & special/chars
```

---

## URL 命令速查

| 操作     | 命令                                     |
| -------- | ---------------------------------------- |
| 提取参数 | `:!cut -d'?' -f2`                        |
| URL 编码 | `:!python -c "import urllib.parse; ..."` |
| URL 解码 | `:!python -c "import urllib.parse; ..."` |
