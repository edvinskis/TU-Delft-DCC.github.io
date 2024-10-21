---
# Insert this YAML header (including the opening and closing ---) at the beginning of the document and fill it out accordingly

# We use this key to indicate the last reviewed date [manual entry, use MM/DD/YYYY]
#date:

# We use this key to indicate the last modified date [automatic entry]
date-modified: last-modified

# Do not modify
lang: en
language: 
  title-block-published: "Last reviewed"
  title-block-modified: "Last modified"

# Title of the document [manual entry]
title: Moving data to your server

# Authors of the document, will not be parsed [manual entry]
author_1:
author_2:

# Maintainers of the document, will not be parsed [manual entry]
maintainer_1:
maintainer_2:

# To whom reach out regarding the document, will not be parsed [manual entry]
corresponding:

# Meaningful keywords, newline separated [manual entry]
categories: 
 - 
 - 

---

## Copy Data from Client to Host using ProxyCommand

```bash
$ scp -o "ProxyCommand ssh -W %h:%p <bastion-username>@linux-bastion-ex.tudelft.nl" <my-local-file>  <target-username>@<target-host>:/<remote-directory>/
```
## Copy Data from Host to Client using ProxyCommand

```bash
$ scp -o "ProxyCommand ssh -W %h:%p <bastion-username>@linux-bastion-ex.tudelft.nl" <target-username>@<target-host>:/tmp/<my-remote-file> /<my-local-directory>/
```

## Copy Data using SSH Tunneling

If a default [ssh tunneling](VPS_SSH.md) was configured correctly. Data can be copied to and from a remote host as follows:

```bash
# Copy TO Remote Host
$ scp <my-local-file> <host-nickname>:/<remote-directory>/
```

```bash
# Copy FROM Remote Host
$ scp <host-nickname>:/<my-remote-file> /<my-local-directory>/ 
```

## scp with sudo files from a remote host to another remote host
"-C /tmp/a" can be used when you wanted to "cd /tmp/a"

```bash
ssh source.tudelft.nl sudo tar cf - -C /tmp/a . | ssh target.tudelft.nl  sudo tar xvf - -C /tmp/b/
```
