#consume 

We can create an Image from the current state of a container by using the following commands:

```bash
docker export -o container.tar <CONTAINER>
```

this will generate a tar archive file. 

Next, we import the tarball:

```bash
docker import [OPTIONS] file|URL|- [REPOSITORY[:TAG]]
```
