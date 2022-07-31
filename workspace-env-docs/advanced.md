# Advanced features

Yes there is more!

## Rootless, rootfull and privileged containers

The general principle is not to run privileged containers. Although there are
times when it's pretty handy to be able to run a privileged container. Think of
certain devices or resources only available on the host itself. Let's be honest,
this setup is a development environment and not a production setup to be
consumed nor exposed to the public. *Also to repeat, do not use this setup for
production use-cases to be consumed or exposed to the public or as a setup to
provide a containerized service*.

If needed, run the following command to run a privileged container. An
alternative to what is shown in [step 4](#step-4):

```shell
podman run -d --rm \
--name podman-ansible-dev-space-example \
--privileged \
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

---

[Home](../README.md) - [Troubleshoot section](troubleshoot.md)