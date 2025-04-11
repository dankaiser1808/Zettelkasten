---
id: sed
aliases: []
tags: []
---

sed gives is an inline text editing tool to manipulate files and strings in Linux without relying on text editors like vim.
```
sed -i -e 's/About/Software/g' /tmp/myfile.xml
```
- -i: changes the file in place. Without it, the result would be printed to stdout
- -e: expression that should be used to manipulate the file

