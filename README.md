# snap-graphpath

This repo contains the sources of the snap `graphpath`.

```
snap install graphpath
```

This snap is just a packaging of the shell script graphpath hosted at
[github.com/ocochard/graphpath](https://github.com/ocochard/graphpath).
The upstream project is a tool for the [BSD Router Project](https://bsdrp.net).
This snap makes most sense to be executed on a server that acts as a router.

## Permissions

The script needs `network-observe` to access the needed network information from
your system. You need to connect that interface to grant graphpath access:

```
snap connect graphpath:network-observe
```

## Example

```
$ graphpath 10.194.34.141 10.90.0.216
+----------------------------+
| SOURCE                     |
| IP:   10.194.34.141        |
| ARP:  9c:67:b1:0b:fd:6b    |
+----------------------------+
              |
+----------------------------+
| IF:   lxdbr0               |
| MAC:  ea:0e:96:0e:11:74    |
| IP:   10.194.34.1          |
| net:  10.194.34.0/24       |
|                            |
|         THIS ROUTER        |
|                            |
| net:  default              |
| IP:   192.168.1.167        |
| MAC:  97:12:14:4e:36:41    |
| IF:   eno1                 |
+----------------------------+
              |
+----------------------------+
| ROUTER                     |
| IP:   192.168.1.1          |
| ARP:  34:c3:7f:53:4d:95    |
+----------------------------+
              |
+----------------------------+
| DESTINATION                |
| IP:   10.90.0.216          |
+----------------------------+
```
