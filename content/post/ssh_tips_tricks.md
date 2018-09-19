+++
date = 2018-02-02
# lastmod = 2017-09-03
draft = false
tags = ["ssh", "tips"]
title = "SSH tips & tricks"
summary = """Quick SSH setup and common question."""
+++

**SSH client setup**

First, you can edit the file .ssh/config in order to define server shortcuts and default options. The file below define *server1* as a standard SSH server, *server2* as a server using a non-default port, *server3* where the server is accessed via an ssh jump by *server2*.

```
Host *
Compression yes
PreferredAuthentications publickey,password 
Protocol 2

Host server1
Hostname server1.com
User user1

Host server2
Hostname server2.com
User user2
Port 653737

Host server3
Hostname server3
User user3
ProxyCommand ssh server2 nc %h %p
```

First, we need to create our own encryption key. 

```
ssh-keygen -t rsa -b 1024
```

**SSH server setup**

