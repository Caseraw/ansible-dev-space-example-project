# Step 2

Get familiar with the example structure and add your own customizations.
Everything can be customized once you get familiar with the setup.

```text
.
├── workspace/                                          [1]
├── workspace-env/                                      [2]
│   ├── containerfiles/                                 [3]
│   ├── containers/                                     [4]
│   └── files/                                          [5]
├── workspace-env-docs/                                 [6]
└── README.md                                           [7]
```

| Number | Description |
|--------|-------------|
| 1 | The actual workspace your project files will reside in. What you'll be working on, on your host machine with VScode or another IDE you work with. |
| 2 | The directory that contains files used for your container image and container. |
| 3 | The directory that contains the container files, used to build container images. |
| 4 | The directory that can contain cache container images, mapped for use within the container. *More about this in the next steps*. |
| 5 | The directory that can contain files to customize a running container, mapped for use within the container. *More about this in the next steps*. |
| 6 | The directory that contains docs and additional docs resources. |
| 7 | The main `README.md` file. |

This example repository comes with a set of example files. These are samples to 
give you a idea of how it can be set up. It's up to you to customize whatever
you like for your setup.

---

[Home](../README.md) - [Prev step (1)](usage-step1.md) - [Next step (3)](usage-step3.md) - [Troubleshoot section](troubleshoot.md) - [Advanced section](advanced.md)