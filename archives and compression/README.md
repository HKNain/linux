# Archives and Compression in Linux

## 1. Archiving

**Archiving** combines multiple files or directories into a single file. The `tar` command is commonly used for archiving.

### Commands

| Command | Description |
|---|---|
| `tar -cf archive.tar folder/` | Creates an archive of a folder. |
| `tar -tf archive.tar` | Lists the contents of an archive. |
| `tar -xf archive.tar` | Extracts an archive. |
| `tar -xf archive.tar -C /path/` | Extracts an archive into a specified directory. |
| `rm -rf folder/` | Deletes a folder and its contents recursively. |

### Examples

Create an archive:

```bash
tar -cf f1.tar fol1/
```

List archive contents:

```bash
tar -tf f1.tar
```

Delete the original folder (the archive remains):

```bash
rm -rf fol1/
```

Extract the archive:

```bash
tar -xf f1.tar
```

**Note:** `tar` archives files but does not compress them by default. Be careful with `rm -rf`, as it permanently deletes files without prompting in normal use.

## 2. Compression

**Compression** reduces file size to save disk space and make file transfers easier.

### Gzip and Gunzip

| Command | Description |
|---|---|
| `gzip file` | Compresses a file into `.gz` format and removes the original file by default. |
| `gunzip file.gz` | Decompresses a `.gz` file. |

Examples:

```bash
gzip file.txt
gunzip file.txt.gz
```

### Zip and Unzip

| Command | Description |
|---|---|
| `zip archive.zip file` | Compresses a file into a ZIP archive. |
| `zip -r archive.zip folder/` | Compresses a folder recursively, including its contents. |
| `unzip archive.zip` | Extracts a ZIP archive. |
| `unzip -l archive.zip` | Lists the contents of a ZIP archive. |

Examples:

```bash
zip archive.zip file.txt
zip -r backup.zip fol1/
unzip backup.zip
unzip -l backup.zip
```

## 3. Tar with Compression

| Command | Description |
|---|---|
| `tar -czf archive.tar.gz folder/` | Creates a gzip-compressed tar archive. |
| `tar -xzf archive.tar.gz` | Extracts a gzip-compressed tar archive. |
| `tar -cjf archive.tar.bz2 folder/` | Creates a bzip2-compressed tar archive. |
| `tar -xjf archive.tar.bz2` | Extracts a bzip2-compressed tar archive. |

## Quick Revision

- `tar -cf` — create an archive.
- `tar -tf` — list archive contents.
- `tar -xf` — extract an archive.
- `gzip` — compress a file.
- `gunzip` — decompress a `.gz` file.
- `zip -r` — compress a directory recursively.
- `unzip` — extract a ZIP archive.
- `rm -rf` — recursively delete a directory and its contents.

**Remember:** Archiving combines files; compression reduces their size.