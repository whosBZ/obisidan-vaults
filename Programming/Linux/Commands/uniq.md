- Used to find repeated lines in a text file or standard input
- If the line of text repeats but is not right after each other then each occurrence is unique

## Flags

- ***-i*** = Case insensitive comparison
- ***-c*** = Shows the count of occurance
- ***-d*** = Only prints duplicated lines
- ***-u*** = Only prints unique lines

## How to find repeated separated lines

- You must first sort a file so that all text that is the same is sequential
- Then you run *uniq* on that output

```bash
sort filename.txt | uniq -d
```