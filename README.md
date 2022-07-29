# Ansible dev space

When it comes to creating Ansible content, it's important to have a reliable
workspace. Workspaces always require some configuration and setup in order to
work with Ansible commands, content etc. Additionally, they should contain tools
to use while developing and troubleshooting. Think of RPM packages, python
dependencies etc. Requirements like these can conflict with the Operating System
(OS) default configuration. This results in tainting the underlying machine and
making it to become a dependency of the project itself. It get's even worse when
it comes to shipping and reliably reproducing these environments on other
machines or workspaces. To add on top of that, it becomes unmanageable when
working with multiple projects that each have different versions and
dependencies that will conflict with each other on the underlying workspace
host.

Containerized workloads provide many advantages such as consistency and built-in
dependencies. It's a widely adopted technology for delivering scalable services.
Many of these advantages can serve well when it comes to creating a development
environment that contains all the requirements and dependencies required for
developing.

Although there are a multitude of alternatives for creating and using confined
workspaces, this project utilizes [podman.io](https://podman.io/) as the
underlying OCI daemonless container engine for developing, managing, and running
OCI Containers on your Linux System.

This repository contains an example project to create a containerized workspace
for creating Ansible content. This example setup can be customized to use for
other purposes than Ansible.

# Requirements

- A host machine capable of reliably running
  [podman.io](https://podman.io/getting-started/installation) without issues.
- Make sure to have [podman.io](https://podman.io/) installed on the host.

> This setup is tried and tested on Fedora 35. *Not tested on MacOS
> and Windows systems*.

# Usage

- [Step 1](workspace-env-docs/usage-step1.md) - Clone this repo to your workspace project directory.
- [Step 2](workspace-env-docs/usage-step2.md) - Add the changes required to your project.
- [Step 3](workspace-env-docs/usage-step3.md) - Build a container image using `podman`.
- [Step 4](workspace-env-docs/usage-step4.md) - Run a podman container using the image.
- [Step 5](workspace-env-docs/usage-step5.md) - Enter the container via an interactive shell.
- [Step 6](workspace-env-docs/usage-step6.md) - Work on your project.
- [Step 7](workspace-env-docs/usage-step7.md) - When done, exit out.
- [Troubleshoot section](troubleshoot.md)
- [Advanced section](advanced.md)