# Step 6

Work on your awesome Ansible project! Do whatever you'd like inside the
container.

Use tools such as `ansible-navigator`. One of the amazing things here is that
`ansible-navigator` itself, uses `podman` to run Ansible execution environments.
So in reality this is an example of using containers inside of containers (as
I'd like to call, container-ception).

Another useful feature is the host-to-container volume mapping of the directory
`/workspace-env/containers:/home/podman/.local/share/containers:Z`. This
provides the possibility to cache container images used within the podman
container on the host for persistency. For example the `ansible-navigator` and
execution environment images don't always have to be pulled from the internet,
*except for the first time*.

Additional host-to-container volume mappings provide the capabilities to 
customize and set up SSH and `.bashrc` configurations within the container. Your
workspace project files are also mapped to the container so they exist within
the container to work on. These features provide persistency without embedding
it in the container image itself. Reducing image size and possible data leaks
such as credentials and tokens.

```shell
$ podman exec -it podman-ansible-dev-space-example bash

Agent pid 118
Identity added: /home/podman/.ssh/id_rsa (podman@8e3779663c4e)

[podman@8e3779663c4e project]$ ansible-navigator 

--------------------------------------------------------------------
Execution environment image and pull policy overview
--------------------------------------------------------------------
Execution environment image name:     quay.io/ansible/creator-ee:v0.4.2
Execution environment image tag:      v0.4.2
Execution environment pull arguments: None
Execution environment pull policy:    tag
Execution environment pull needed:    True
--------------------------------------------------------------------
Updating the execution environment
--------------------------------------------------------------------
Running the command: podman pull quay.io/ansible/creator-ee:v0.4.2
Trying to pull quay.io/ansible/creator-ee:v0.4.2...
Getting image source signatures
Copying blob 9313088620cb done  
Copying blob 9f45cf1cd9f2 done  
Copying blob fee18ea417d6 done  
Copying blob f0a2109a2528 done
...
...
...
```

![ansible-navigator](images/ansible-navigator-sample-screen.png)

```shell
[podman@8e3779663c4e project]$ podman images

REPOSITORY                  TAG         IMAGE ID      CREATED       SIZE
quay.io/ansible/creator-ee  v0.4.2      12571ac947cf  3 months ago  2.4 GB
```

---

[Home](../README.md) - [Prev step (5)](usage-step5.md) - [Next step (7)](usage-step7.md) - [Troubleshoot section](troubleshoot.md) - [Advanced section](advanced.md)