### Tar-ing
```console
# Untar
$ tar -xvzf filename.tar.gz
```
-z  decompress uzing gzip <br>
-x  extract <br>
-v  verbose <br>
-f  filename (followed by filename) <br>


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

# Delete from shortest front pattern
$ echo ${PATH#/*/}
to/file.ext
$ echo ${PATH#/*to}
/file.ext

```

### Useful sed commands

```bash
# delete lines containing pattern
sed '/pattern/d' file.txt

# keep backup called file.txt.backup when modifying in place
sed -i.backup 's/pattern/replacement/' 


```

### Using grep as a conditional 
```bash 
if echo $PATTERN | grep -q file.txt; then 
  echo "Match"
fi 

```


### Useful inbuilt bash variables
- $PWD
- $$         - process id of the script (will return parent process id)
- $BASHPID   - process id of current instance of bash (will include a subshell)
- $HOSTNAME  - host name
- $HOME      - home directory
- $#         - number of arguments passed to a script
- $!         - process id of last job run in background
```console
$ echo $PWD
/path/to/currentdirectory
$ echo ${PWD##*/}
currentdirectory
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


