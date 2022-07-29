# Step 3

Have a look at the [Containerfile](../workspace-env/containerfiles/Containerfile).
The base image is derived from the original [podman
image](https://quay.io/podman/stable:latest). On top of that image, several RPM
packages as well as python packages are installed and set up for use with the
`podman` user. Apply your own changes as much as you'd like. *Keep in mind that
it's originally based on the podman image*.

* Build the container image using `podman`:

```shell
podman build -f workspace-env/containerfiles/Containerfile -t ansible-dev-space-example-image:lab01
```

* Check the podman image list:

```shell
$ podman images

REPOSITORY                                 TAG         IMAGE ID      CREATED         SIZE
localhost/ansible-dev-space-example-image  lab01       8b86cc7e99e8  36 seconds ago  946 MB
quay.io/podman/stable                      latest      808669753c20  22 hours ago    349 MB
```

> Make sure to build new images from time to time to ensure forward
> compatibility of your containerized workspace. Additionally push the image to
> a registry where it can be stored centrally and consumed by a the audience
> that need it.

---

[Home](../README.md) - [Prev step (2)](usage-step2.md) - [Next step (4)](usage-step4.md) - [Troubleshoot section](troubleshoot.md) - [Advanced section](advanced.md)