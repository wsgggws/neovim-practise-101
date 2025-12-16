## 70. 查看当前行 Git blame

```python
def hello():  # 查看这行是谁在什么时候修改的
    pass
```

## 71. 查看文件 Git diff

```python
def hello():
-    print("old")
+    print("new")
```

## 72. 跳转到冲突位置

```python
<<<<<<< HEAD
version_a = 1
=======
version_b = 2
>>>>>>> branch
```

=> 快速定位到冲突标记处
