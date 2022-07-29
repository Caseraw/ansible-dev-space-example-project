### Step 7

When done, exit out of the running container. Log in at a later time (if the
container is still running). Remove the container, redeploy the container. Do
whatever you'd like. As long as the files you value, are stored safely on host
using host-to-container volume mappings.

When running the `podman run` command with the additional parameters, you've
noticed the `--rm` flag. This ensures the removal of a stopped container. The
general philosophy behind this is that everything has to be reproducible. You
can customize whatever you'd like, as long as it's reproducible when redeploying
the the container.

> *Containers are cattle! Don't tread them as pets*.

---

[Home](../README.md) - [Prev step (6)](usage-step6.md) - [Troubleshoot section](troubleshoot.md) - [Advanced section](advanced.md)