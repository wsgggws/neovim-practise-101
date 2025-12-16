## 76. SQL 查询格式化

```sql
SELECT id,name,email FROM users WHERE age>18 AND status='active'
```

=>

```sql
SELECT
    id,
    name,
    email
FROM users
WHERE age > 18
  AND status = 'active'
```

## 77. SQL 关键字大写

```sql
select * from users where id = 1
```

=>

```sql
SELECT * FROM users WHERE id = 1
```
