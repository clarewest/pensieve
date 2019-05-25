### Taring
```console
# Untar
$ tar -xvzf filename.tar.gz
```
-z  decompress uzing gzip
-x  extract 
-v  verbose
-f  filename (followed by filename)


### Path manipulation

``` console 
# Strip directory and suffix from filenames 
$ basename /path/to/file.tar.gz 
file.tar.gz

# Can also remove a suffix
$ basename /path/to/file.tar.gz .gz 
file.tar

$ PATH=/path/to/file.ext
$ echo ${PATH%.ext}
/path/to/file

# Delete from last pattern, e.g. to remove file extension
$ echo ${PATH%.*}
/path/to/file
$ echo ${PATH%file*}
/path/to/

# Delete from shortest front patter
$ echo ${PATH#/*/}
to/file.ext
$ echo ${PATH#/*to}
/file.ext

```

### Cores in use per user
```console
$ ps r -eo euser | grep -v EUSER | sort | uniq -c
      3 someoneelse
      1 west
```

### Unwrap fasta files
``` bash
sed ':a; $!N; /^>/!s/\n\([^>]\)/\1/; ta; P; D' FILENAME
```

### Round all numbers in a file to 2dp
```bash
awk '{
    while (match($0, /[0-9]+\.[0-9]+/)) {
        printf "%s%.2f", substr($0, 1, RSTART-1), substr($0, RSTART, RLENGTH)
        $0 = substr($0, RSTART+RLENGTH)
    }
    print
}'
```

### Iterate over lines in a file

```bash
while read LINE; do
  echo $LINE
done <file.txt

```


