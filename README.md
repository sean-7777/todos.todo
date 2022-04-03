# Todos.todo
The [todo.txt format](https://github.com/todotxt/todo.txt) is great, but it has some missing features. This document aims to provide a extended and more detailed form of the todo.txt format. Like the original, it is also purely plain ASCII text. When Markdown is used, it is [GitHub flavored Markdown](https://github.github.com/gfm/).



## Wrapping
When a value is being wrapped, ex. in `{}`, it cannot contain any of it's wrapping characters, ex. `{` and `}`[^future-add].



## Location
Todos should be stored in a folder, `~\todos` preferably. Each file should represent a todo list, and should be named as `listname.todo`.



## Task Line Syntax
Each task line is divided into sections, some optional. They are all seperated by a space.

### Project
This is an optional section, and allows the list to be split into several smaller sections. The project name should be `PascalCased`, and be wrapped with `{}`, like `{MyProject}` and `strict-style`.


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


### Reference
This contains the reference ID used when referencing.


### Task
Following the date, should be the task. The task should be a short, one-sentence summary of the task, and should not end with a period. It is also allowed to have Markdown for formatting.


### Tags
Tags are things that can be used to `Ctrl+F` tasks quickly. They are similar to a internet hashtag, and should be prefixed with one, such as `#shopping`. They should use `flatcase` and `strict-style`.


### Description
Another optional section, and is used when a task needs more instructions than provided with the task section. The task line should end with a `$` to notate that a description is provided, and the description should be provided on a indented new line(s). The indention should be four spaces. Markdown is available here also.



## References
Across the task lines, references can be used where ever text is used. They are prefixed with a `@` and should contain the reference ID. The reference id should be `kebab-case`, and strict-style with dashes. References are not only limited to tasks, they can also reference external resources by defining a reference section at the top.


### Reference Section
The reference section is a optional section used at the top of a document used to link external resources to references. It should be surrounded by `-----` (5 dashes) on their own lines. In between should be the reference section. Each reference link should first start with the name. The name and value of a reference link is seperated with a `:=` or `=`. 

If `:=`, it is a reference to an set resource, such as links, webpages, user profiles, etc... The values it can contain are listed as follows[^future-more].
- Links: Wrapped in `{}`.
- Emails: Wrapped in `<>`. Can contain a name by adding another `<>`, like `<johndoe@example.com><John Doe>`.

If `=`, then it is a reference to a inferred resource, which is a plain text string, which could be things like names and books, but without any specific link. With inferred resources, the value should be wrapped in `""`.




## An example
```

```




[^future-add]: This most likely will be supported in future revisions.
[^future-more]: This most likely will have more in future revisions.
