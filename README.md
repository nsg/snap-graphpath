# snap-graphpath

[![Snap Status](https://build.snapcraft.io/badge/nsg/snap-graphpath.svg)](https://build.snapcraft.io/user/nsg/snap-graphpath)

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

## Report a bug/problem

This repository only package the upstream project. If you think you have found
a problem with graphpath, first make sure that it works outside the security
sandbox that snapd provides.

* Execute the script directly, for example `/snap/graphpath/current/bin/graphpath`
  or possible `/var/lib/snapd/snap/current/bin/graphpath`.

If this works, the problem is in the packaging, feel free to open an
[issue](https://github.com/nsg/snap-graphpath/issues) and report the problem.
Still the same problem? Open a upstream issue at
[ocochard/graphpath](https://github.com/ocochard/graphpath/issues) and report
the issue.

### New version?

Make a PR that updates [this line](https://github.com/nsg/snap-graphpath/blob/master/snap/snapcraft.yaml#L4) or open a [issue](https://github.com/nsg/snap-graphpath/issues).

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
