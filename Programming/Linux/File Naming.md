## Dashed File Names
- If a file is named with a hypen as its first character it can cause issues
- If you want to access them you can use a full or relative path structure to access them

```bash
cat ./-badFile
```

## Spaces in File names
- To access a file with spaces in its name, you must use quotation marks to access them

```bash
cat "Spaces In File Name"
```

- Dashes can cause issues here too, so you must use the previous relative or full path as you would for dashed file names
- Without this some terminals interpret it as flags even with quotations

```bash
cat ./"--Spaces in file name--""
```

- You can also use backslashes to escape the spaces and ensure the terminal interprets the full spaces without quotations

```bash
cat Spaces\ In\ File\ Name
```