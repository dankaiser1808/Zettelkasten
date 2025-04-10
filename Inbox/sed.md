sed gives us the option to manipulate files and strings in linux without relying on text editors like vim.
It gives us inline option to directly change a files strings with regular expressions


```
sed -i -e 's/About/Software/g' /tmp/myfile.xml
```

- -i: changes the file in place. Without it, the result would be printed to stdout
- -e: expression that should be used to manipulate the file

