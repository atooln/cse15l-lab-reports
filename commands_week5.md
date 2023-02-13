# Find
## `-type`
The ``-type`` option can be used to search for files based on their type, such as regular files, directories, symbolic links, sockets, etc. Here are two examples:

```
$ find ./written_2 -type f  # find all files in the directory
    ./written_2/non-fiction/OUP/Berk/ch2.txt
    ./written_2/non-fiction/OUP/Berk/ch1.txt
    ./written_2/non-fiction/OUP/Berk/CH4.txt
    ./written_2/non-fiction/OUP/Berk/ch7.txt
    ./written_2/non-fiction/OUP/Abernathy/ch2.txt
    ...
```
This command finds all regular files in ``./written_2`` directory. This can be useful in finding all files within the sub directories of ``./written_2``

```
$ find ./written_2 -type d  # find all directories in the directory
    ./written_2
    ./written_2/non-fiction
    ./written_2/non-fiction/OUP
    ./written_2/non-fiction/OUP/Berk
    ./written_2/non-fiction/OUP/Abernathy
    ...
```
This command finds all the sub directories in ``./written_2``. This can be useful in finding all of the sub directories of ``./written_2``

Source: [Linuxize](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/)

## `-size`
The ``-size`` option can be used to search for files based on their size. Here are two examples:


```
$ find ./written_2 -size +2k # find files larger than 2KB
    ./written_2/non-fiction/OUP/Berk/ch2.txt
    ./written_2/non-fiction/OUP/Berk/ch1.txt
    ./written_2/non-fiction/OUP/Berk/CH4.txt
    ./written_2/non-fiction/OUP/Berk/ch7.txt
    ./written_2/non-fiction/OUP/Abernathy/ch2.txt
    ...
```
This command finds all files in ``./written_2 directory`` larger than 2KB. This can be useful in finding files greater than a particular size
```
$ find ./written_2 -size -1k # find files smaller than 1KB
    ./written_2
    ./written_2/non-fiction
    ./written_2/non-fiction/OUP
    ./written_2/non-fiction/OUP/Berk
    ./written_2/non-fiction/OUP/Abernathy
    ...
```
This command finds all files in ``./written_2 directory`` smaller than 1KB. This option can be useful if you want to find files of a specific size range.

Source: [find man page](https://man7.org/linux/man-pages/man1/find.1.html)

## `-mtime`
The ``-mtime`` option can be used to search for files based on their modification time. Here are two examples:

```
$ find ./written_2 -mtime -1 # find files modified < 24 hours ago
    ./written_2
    ./written_2/non-fiction
    ./written_2/non-fiction/OUP
    ./written_2/non-fiction/OUP/Berk
    ./written_2/non-fiction/OUP/Berk/ch2.txt
```
This command finds all files in ``./written_2`` directory modified less than 24 hours ago. This can be useful in finding files that were recently created of modified
```
$ find ./written_2 -mtime +1 # find files modified > 24 hours ago

```

This command finds all files in ``./written_2`` directory modified more than 24 hours ago. This option can be useful if you want to find files that were recently modified or not modified for a long time. Since I cloned the ``./written_2`` repo as I was creating this document, there are no files that were modified more than 24 hours ago.

Source: [find man page](https://man7.org/linux/man-pages/man1/find.1.html)

## ``-exec``
The`` -exec`` option can be used to execute a command on the files found by find. Here are two examples:

```
$ find ./written_2 -type f -name "*.txt" -exec cat {} \; # print the content of all .txt files
    House, practically imploring you to sit on the furniture. Try to disregard the poorly realized reproductions of original wall murals around the courtyard.
    Across the square is the elegant Hotel Casa Granda, which opened in 1914. Its terrace bar on the fifth floor affords excellent views of the cathedral towers and the city beyond.
    East from the square, Calle Heredia is the epicenter of Santiago culture and tourism. The city’s famous Casa de la Trova (music hall), 
    ...
```
This prints the content of all .txt files in ``./written_2`` directory. This could be useful if you want to see the output of all files or even a single file deep in the directory structure. 

```
$ find ./written_2 -type f -name "ch1.txt" -exec rm {} \; # delete ch1.txt file

$ find ./written_2 -type f -name "ch1.txt"
```
This command deletes the `ch1.txt` file. This option can be useful if you want to delete (or try any other action) to one or multiple files deep in the directory structure.

Source: [The Linux Documentation Project](https://tldp.org/LDP/GNU-Linux-Tools-Summary/html/x9543.htm)