```dataview
TABLE WITHOUT ID
file.link AS Homework
FROM "Projects"
WHERE Category = "Homework"
SORT file.mtime DESC
LIMIT 10
```
```dataview
TABLE WITHOUT ID
file.link AS LessonNotes
FROM "Projects"
WHERE Category = "LessonNotes"
SORT file.mtime DESC
LIMIT 10
```
```dataview
TABLE WITHOUT ID
file.link AS Planning
FROM "Projects"
WHERE Category = "Planning"
SORT file.mtime DESC
LIMIT 10
```
```dataview
TABLE WITHOUT ID
file.link AS Project
FROM "Projects"
WHERE Category = "Project"
SORT file.mtime DESC
LIMIT 10
```
```dataview
TABLE WITHOUT ID
file.link AS Research
FROM "Projects"
WHERE Category = "Research"
SORT file.mtime DESC
LIMIT 10
```
```dataview
TABLE WITHOUT ID
file.link AS Thoughts
FROM "Projects"
WHERE Category = "Thoughts"
SORT file.mtime DESC
LIMIT 10
```
