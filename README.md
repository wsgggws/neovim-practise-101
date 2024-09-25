# neovim-practise-101

## 1. 删除空行

```text


MacBook Air (M2, 2022 16GB)

MacOS Monterey 12.6.6

NVIM v0.9.0

plugins manager: https://github.com/folke/lazy.nvim


template: https://www.lazyvim.org/

my config: https://github.com/wsgggws/nvim

some requirements: https://github.com/wsgggws/dotfiles/tree/main/brew
NVIM v0.9.0



```

=>

```text
MacBook Air (M2, 2022 16GB)
MacOS Monterey 12.6.6
NVIM v0.9.0
plugins manager: https://github.com/folke/lazy.nvim
template: https://www.lazyvim.org/
my config: https://github.com/wsgggws/nvim
some requirements: https://github.com/wsgggws/dotfiles/tree/main/brew
NVIM v0.9.0
```

## 2. 删除重复行

=>

```text
MacBook Air (M2, 2022 16GB)
MacOS Monterey 12.6.6
NVIM v0.9.0
plugins manager: https://github.com/folke/lazy.nvim
template: https://www.lazyvim.org/
my config: https://github.com/wsgggws/nvim
some requirements: https://github.com/wsgggws/dotfiles/tree/main/brew
NVIM v0.9.0
```

## 3. 添加递升/递减序号

```text
1
2
3
4
```

=>

```text
1. 1
2. 2
3. 3
4. 4

or

4. 1
3. 2
2. 3
1. 4
```

## 4. 倒置文本行

```text
1111111
3333333
2222222
4444444
```

=>

```text
4444444
2222222
3333333
1111111
```

## 5. 行排序

```text
case 1
4
2
3
1

case 2
4.1
2.4
3.2
1.3
```

=>

```text
case 1
1
2
3
4

or

4
3
2
1

case 2
4.1
3.2
1.3
2.4

```

## 6. 更改文本对象内容

```text
# 请更改 value 为 wsgggws
{"key": "value"} => {"key": "wsgggws"}
```
