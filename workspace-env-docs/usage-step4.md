# Step 4

Run a container with `podman` using the image:

```shell
podman run -d --rm \
--name podman-ansible-dev-space-example \
--security-opt label=disable \
--security-opt unmask=ALL \
--userns=keep-id \
--user podman \
-v ./workspace-env/containers:/home/podman/.local/share/containers:Z \
-v ./workspace-env/files/ssh:/home/podman/.ssh:Z \
-v ./workspace-env/files/bashrc:/home/podman/.bashrc:Z \
-v ./workspace:/home/podman/project:Z \
localhost/ansible-dev-space-example-image:lab01 \
sleep infinity
```

Check the running pods:

```shell
$ podman ps -a

CONTAINER ID  IMAGE                                            COMMAND         CREATED         STATUS             PORTS       NAMES
8e3779663c4e  localhost/ansible-dev-space-example-image:lab01  sleep infinity  13 seconds ago  Up 11 seconds ago              podman-ansible-dev-space-example
```

> Pay attention to the host-to-container volume mappings, these can be pretty
> handy! Also, note the `--rm` parameter. *More about this in the next steps*.

> If things don't work at the first try, check the
> [troubleshoot section](troubleshoot.md) section for additional resources.

---

[Home](../README.md) - [Prev step (3)](usage-step3.md) - [Next step (5)](usage-step5.md) - [Troubleshoot section](troubleshoot.md) - [Advanced section](advanced.md)