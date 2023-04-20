# 今日新增
```dataview
table file.ctime
where file.ctime >= date(today) 
sort file.mtime desc
```
# 今日修改
```dataview
table file.mtime 
WHERE file.mtime >= date(today)
```