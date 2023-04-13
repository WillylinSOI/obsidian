# Discription


# Check list
- [ ] 
- [ ] 

```dataviewjs  
const Title = dv.current().file.name  
const kbfile = Title
const Tasks = dv.page(kbfile).file.tasks  
let NumberOfTasks = Tasks.length || 1  
let CompletedTasks = Tasks.where(t => t.completed)  
dv.span("![progress](https://progress-bar.dev/" + parseInt((CompletedTasks.length / NumberOfTasks) * 100) + "/)" )  
```
---
```button
name new comment
type append template
action kanban new comment template
```
