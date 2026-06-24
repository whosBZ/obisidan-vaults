- The `find` command in Linux is used to search for files and directories based on name, type, size, date, or other conditions. It scans the specified directory and its sub directories to locate files matching the given criteria.

## Using with commands like du

- To get a list of file sizes you can pass the results using the -exec command

```bash
find . -type f -size 1033c -exec du -b {} +
```

- The above command takes all files in the current directory and sub directories using the period
- the -type f only lists files and ignores directories, symlinks and devices
- The -size limits it to 1033c which is 1033 bytes
- the -exec will run du on every file found like a loop
- the {} is replaced by each of the file names to work on
- The + optimizes the output to group it all as one command

## Find File by username or group

- By just username

```bash
find /path/to/directory -user username
```

- By just group

```bash
find /path/to/directory -group groupname
```

- By both username and group

```bash
find /path/to/directory -user username -group groupname
```