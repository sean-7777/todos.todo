# Todos.todo
The [todo.txt format](https://github.com/todotxt/todo.txt) is great, but it has some missing features. This document aims to provide a extended and more detailed form of the todo.txt format. Like the original, it is also purely plain ASCII text. When Markdown is used, it is [GitHub flavored Markdown](https://github.github.com/gfm/).



## Wrapping
When a value is being wrapped, ex. in `{}`, it cannot contain any of it's wrapping characters, ex. `{` and `}`[^future-add].



## Location
Todos should be stored in a folder, `~\todos` preferably. Each file should represent a todo list, and should be named as `listname.todo`.



## Metadata
Each list can contain metadata. Each line of metadata is prefixed with `|`, and the name and value are seperated with a `=`. Example: `| author = john doe`. Names are `strict-style` and are `pascalCase`. Values are Markdown and can be multiline if a `$` is used, the value will be on the next lines with a four space indention. Common names:
- `author`
- `description`
- `importance`



## References
Across the task lines, references can be used where ever text is used. They are prefixed with a `@` and should contain the reference ID. The reference id should be `kebab-case`, and strict-style with dashes. References are not only limited to tasks, they can also reference external resources by defining a reference section at the top.


### Reference Section
The reference section is a optional section used at the top of a document used to link external resources to references. It should be surrounded by `-----` (5 dashes) on their own lines. In between should be the reference section. Each reference link should first start with the name. The name is `pascalCase` and `strict-style`. The name and value of a reference link is seperated with a `:=` or `=`. 

If `:=`, it is a reference to an set resource, such as links, webpages, user profiles, etc... The values it can contain are listed as follows[^future-more].
- Links: Wrapped in `{}`.
- Emails: Wrapped in `<>`. Can contain a name by adding another `<>`, like `<johndoe@example.com><John Doe>`.

If `=`, then it is a reference to a inferred resource, which is a plain text string, which could be things like names and books, but without any specific link. With inferred resources, the value should be wrapped in `""`.



## Task Block
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


### Metadata
Aditional metadata not provided by the optional sections can be included here. They are seperated with a `:`, ex. `people:john,max`. The names are `strict-style` and are `pascalCase`. The values are `strict-style` with these characters: `,_~-`.


### Description
Another optional section, and is used when a task needs more instructions than provided with the task section. The task line should end with a `$` to notate that a description is provided, and the description should be provided on a indented new line(s). The indention should be four spaces. Markdown is available here also.



## An example
```
WORK IN PROGRESS
```



## Extended Backus-Naur Grammar
```ebnf
todo file = [ metadata ], [ reference section ], task block;

space = [ " " ];
nl = "\n";
letters = "a" | "b" | "c" | "d" | "e" | "f" | "g" | "h" | "i" | "j" | "k" | "l" | "m" | "n" | "o" | "p" | "q" | "r" | "s" | "t" | "u" | "v" | "w" | "x" | "y" | "z" | "A" | "B" | "C" | "D" | "E" | "F" | "G" | "H" | "I" | "J" | "K" | "L" | "M" | "N" | "O" | "P" | "Q" | "R" | "S" | "T" | "U" | "V" | "W" | "X" | "Y" | "Z";
nums = "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9";
strict = letters | nums;
chars = strict | "~" | "!" | "@" | "#" | "$" | "%" | "^" | "&" | "*" | "(" | ")" | "_" | "+" | "{" | "}" | "|" | ":" | '"' | "<" | ">" | "?" | "`" | "-" | "=" | "[" | "]" | ";" | "'" | "," | "." | "/";

metadata = { meta line, nl };
meta line = "| ", space, "=", space, { char }-;

reference section = ref sep, nl, { ref line, nl }-, ref sep;
ref line = { strict }-, space, (":=", space, set ref) | ("=", space, infer ref);
set ref = ? url ? | ? email ?;
infer ref = '"', { char }, '"';
ref sep = "-----";

url = "http", { "s" }, "://", strict, { strict | "-" }, [ ":", nums ], { "/", letters | nums | "-" | "." | "_" | "~" | "!" | "$" | "&" | "'" | "(" | ")"\             | "*" | "+" | "," | ";" | "=" }, [ "?", { chars }-, "=", { chars-"&" }- ], [ "#", { chars }- ];
```



## Terminology
These are definitions for terms used throughout the document.

#### `strict-style`
> This is a term used for naming purposes. Something that is `strict-style` only has numbers 0-9, and the latin alphabet (uppercase and lowercase). If something is said to be `strict-style` with something, that something is also included in the limited set of characters allowed.
#### `reference`
> Section: The block where references are contained.
> Link: A line in the reference section
#### `resource`
> Inferred: A plain text resource.
> Set: A resource with a pointing value.
#### `Task`
> Line: A line in the task block.
> Block: The majority section of the document, where tasks are defined.



[^future-add]: This most likely will be supported in future revisions.
[^future-more]: This most likely will have more in future revisions.
