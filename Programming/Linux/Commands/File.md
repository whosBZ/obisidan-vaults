- Used to list information about a given file or list of files

## Useful Flags

- **--** = Can be used to interpret piped strings as a file path 
```bash
find . -type f | file -- *
```