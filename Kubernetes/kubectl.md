Communicates with control plane via API on user's behalf

Basic Commands (Beginner):
| Command | Description                                                               |
| ------- | ------------------------------------------------------------------------- |
| create  | Create a resource from a file or from stdin                               |
| expose  | Expose a replication controller, svc, deployment, or pod as a new service |
| run     | Run a particular image on the cluster                                     |
| set     | Set specific features on objects                                          |
| explain | Get documentation for a resource                                          |
| get     | Display one or many resources (`get nodes`, `get events`, ...)                                             |
| edit    | Edit a resource on the server                                             |
| delete  | Delete resources                                                          |

Deploy Commands:
| Command   | Description                      |
| --------- | -------------------------------- |
| rollout   | Manage the rollout of a resource |
| scale     | Set a new size for a resource    |
| autoscale | Auto-scale a resource            |

Cluster Management Commands:
| Command           | Description                            |     |
| ----------------- | -------------------------------------- | --- |
| certificate       | Modify certificate resources           |     |
| cluster-info      | Display cluster information            |     |
| cluster-info dump | JSON Dump of cluster information       |     |
| top               | Display resource (CPU/memory) usage    |     |
| cordon            | Mark node as unschedulable             |     |
| uncordon          | Mark node as schedulable               |     |
| drain             | Drain node in prep for maintenance     |     |
| taint             | Update the taints on one or more nodes |     |

Troubleshooting and Debugging Commands:
| Command      | Description                                  |
| ------------ | -------------------------------------------- |
| describe     | Show details of a specific resource or group |
| logs         | Print the logs for a container in a pod      |
| attach       | Attach to a running container                |
| exec         | Execute a command in a container             |
| port-forward | Forward local port(s) to a pod               |
| proxy        | Run a proxy to the K8s API Server            |
| cp           | Copy files and dirs to/from containers       |
| auto         | Inspect authorization                        |
| debug        | Create debugging sessions                    |

  Advanced Commands:
  | Command   | Description                                              |
  | --------- | -------------------------------------------------------- |
  | diff      | Diff the live version against a would-be-applied version |
  | apply     | Apply a configuration to a resource by filename or stdin |
  | patch     | Update fields of a resource                              |
  | replace   | Replace a resource by filename or stdin                  |
  | wait      | Wait for a condition on one or many resources            |
  | kustomize | Build a kustomization target from a directory or URL     |
  
Settings Commands:
| Command    | Description                              |
| ---------- | ---------------------------------------- |
| label      | Update the labels on a resource          |
| annotate   | Update the annotations on a resource     |
| completion | Output shell completion code for a shell |

Other Commands:
| Command       | Description                                 |
| ------------- | ------------------------------------------- |
| alpha         | Commands for features in alpha              |
| api-resources | Print supported API resources on the server |
|  api-versions  |  Print the supported API versions on the server, in the form of "group/version"|
| config  | Modify kubeconfig files                         |
| plugin  | Provides utilities for interacting with plugins |
| version | Print the client and server version information |

