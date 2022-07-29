# Troubleshoot

If you encounter issues, always check whether you are running the latest stable
release of [podman.io](https://podman.io/releases/)

## subuid and subgid

```
ERRO[0000] cannot find UID/GID ..........
WARN[0000] Using rootless single mapping into the namespace ..........
```

The above error occurs due to the absence of the subuid and subgid range of the
use running the podman container.

Solve this with:

```shell
sudo usermod --add-subuids 10000-75535 --add-subgids 10000-75535 <YOUR-USER>

exec $SHELL

podman system migrate

podman system reset
```

## File permissions and ownership

Although the host-to-conatiner volume mappings are pretty handy, they might not
always work straight of the box. The ownership of file are is inherited within
the container. The UID and GID of the files will differ from the user within the
container. To work around this issue, use ACL's.

```shell
podman unshare setfacl -Rm o::rwX <PATH-TO-FILE-OR-DIR>

podman unshare setfacl -Rdm o::rwX <PATH-TO-FILE-OR-DIR>
```

```shell
podman unshare setfacl -Rm o::rwX workspace

podman unshare setfacl -Rdm o::rwX workspace

podman unshare setfacl -Rm o::rwX workspace-env

podman unshare setfacl -Rdm o::rwX workspace-env
```

# Resources

- https://docs.podman.io/en/latest/markdown/podman.1.html
- https://docs.podman.io/en/latest/markdown/podman-run.1.html
- https://github.com/containers/podman/blob/main/docs/tutorials/rootless_tutorial.md
- https://access.redhat.com/solutions/6161832
- https://access.redhat.com/solutions/6216591

---

[Home](../README.md) - [Advanced section](advanced.md)