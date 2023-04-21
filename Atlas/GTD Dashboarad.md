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

## Tasks 近期未來事項
```tasks
starts before tomorrow
due in this week
has due date
path includes Spaces/Life/Projects
path does not include Spaces/Life/Projects/生活/2023個人OGSM.md
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

## Tasks 工具分類手機
```tasks
starts before tomorrow
tags include 條件或設備/手機
path includes Spaces/Life/Projects
sort by due
```


## Tasks 未歸檔檢視
```tasks
description does not include 🛫
description does not include 📅
no tags
not done
path includes Spaces/Life/Projects
path does not include Spaces/Life/Projects/生活/2023個人OGSM.md
group by folder
```

## Tasks 要買的東西
```tasks
heading includes 要買的物品
path includes Spaces/Life/Projects
```

## Tasks OGSM
```tasks
path includes Spaces/Life/Projects/生活/2023個人OGSM.md
sort by due 
```


## Tasks 所有未來事項
```tasks
starts before tomorrow
has due date
path includes Spaces/Life/Projects
path does not include Spaces/Life/Projects/生活/2023個人OGSM.md
sort by due
group by folder
```


## Tasks 一般雜項
```tasks
heading includes 一般雜項
path includes Spaces/Life/Projects
```

## Tasks 等待清單
```tasks
tags include 等待
path includes Spaces/Life/Projects
group by folder
```

## Tasks 未來清單
```tasks
tags include 未來可能
path includes Spaces/Life/Projects
group by folder
```

## Tasks 所有清單
```tasks
path includes Spaces/Life/Projects
group by folder
```

# Reference

---
[GTD-METADATA](GTD-METADATA.md)
