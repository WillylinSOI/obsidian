#GTD-METADATA

---
# view 

## All Area File
```dataview 
TABLE area,Start_Date,Due_Date,Duration,精力,重要性,類型,任務狀態,等待 
FROM "Spaces/Life/Projects"
WHERE 任務狀態 != "完成"
SORT area
```

## Tasks 要買的東西
```tasks
heading includes 要買的物品
path includes Spaces/Life/Projects
```

## Tasks 一般雜項
```tasks
heading includes 一般雜項
path includes Spaces/Life/Projects
```

## Tasks 未來事項
```tasks
starts before tomorrow
has due date
path includes Spaces/Life/Projects
sort by due
group by folder
```

## Tasks 重要事項
```tasks
starts before tomorrow
tags include 重要性/
path includes Spaces/Life/Projects
sort by due
```

## Tasks 等待清單
```tasks
tags include 等待
path includes Spaces/Life/Projects
group by folder
```

## Tasks 未歸檔檢視
```tasks
no tags
no due date
no start date
not done
no scheduled date
path includes Spaces/Life/Projects
path does not include Spaces/Life/Projects/kanban/
```

description does not include
# Reference

---
[GTD-METADATA](GTD-METADATA.md)
