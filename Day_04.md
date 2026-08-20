## Day 4 - awk, sed, find

Shorter day today, but covered a few key text-processing tools.

### awk

```bash
awk '{print}' file_name                         # print whole file
awk '/text_to_find/ {print}' file_name          # print only matching lines
awk '/text_to_find/ {print $1,$2}' file_name    # print specific columns from matches

# head/tail work with awk output too
awk '{print}' file_name | head -n 5
awk '{print}' file_name | tail -n 5

# conditions inside awk
awk '{if ($1=="july" && $2=="11") print $3,$4}' file_name
```

### grep vs awk
- `grep` - regex pattern matching, finds lines
- `awk` - programmatic, supports conditions and column-level filtering

### sed (stream editor)

```bash
sed 's/text_to_replace/replacement/g' file_name     # preview only, doesn't save
sed -i 's/text_to_replace/replacement/g' file_name  # -i edits file in place, saves changes
```
`s` = substitute, `g` = globally

### find

```bash
find . -name file_name   # . = current directory
```

### Next up
More Linux commands + networking commands.
