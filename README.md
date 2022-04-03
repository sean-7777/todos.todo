# Todos.todo
The [todo.txt format](https://github.com/todotxt/todo.txt) is great, but it has it's issues for me. This document aims to provide a extended form of the todo.txt format. Like the original, it is also purely plain ASCII text.


## Location
Todos should be stored in a folder, `~\todos` preferably. Each file should represent a todo list, and should be named as `listname.todo`.


## Syntax
### Project
This is an optional section, and allows the list to be split into several smaller sections. The project name should be `CamelCased`, and be wrapped with `{}`, like `{MyProject}`.

### Status
Each todo should first start out with a `[]` if uncompleted, if completed a `[X]`. It can optionally contain a percentage such as `[40%]` to notate partial completion.

### Priority
The priority of the task should be put after the status, in `()`. The priority levels are as follows.
```
!!, S, A, B, C, D, F, Z
```

### Date
After the priority should be the date. Only the completion date is required.
```
<creationdate -- enddate | duedate>
```
The date format should be: `YYYY/MM/DD`.

### Task
Following the date, should be the task. The task should be a short, one-sentence summary of the task, and should not end with a period.

### Tags
Tags are things that can be used to find `ctrl+f` tasks quickly. They are similar to a internet hashtag, and should be prefixed with one, such as `#shopping`.

### An example
```

```
