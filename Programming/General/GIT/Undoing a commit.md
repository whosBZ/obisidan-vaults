## Remove commit and moves back to staging step without rolling back files

```bash
git reset --soft HEAD~1
```
- Moves the HEAD one commit backwards.
- Keeps previously staged files in staged.

## Remove commit and unstage commited files without removing changes

```bash
git reset HEAD~1
```
- Moves the HEAD one commit backwards.
- Removes the staged files.
## Removes commit and rolls back all changes to previous commit

```bash
git reset --hard HEAD~1
```
- Moves the HEAD one commit backwards
- Reverts all files to that commits point in time
- Very dangerous and can lose a lot of work

