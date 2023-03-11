Small, testing/learning/dev version of Kubernetes in a virtualized environment.

Commands to start with:
```
minikube start
minikube status
minikube dashboard --url
minikube service hello-node
```


Basic Commands:
| Command   | Description                                                          |
| --------- | -------------------------------------------------------------------- |
| start     | Start the k8s cluster                                                |
| status    | Get status of running cluster                                        |
| stop      | Stops the k8s cluster                                                |
| delete    | Deletes the cluster                                                  |
| dashboard | Run and access the 'dashboard' cluster app which manages the cluster |
| pause     | Pause the k8s cluster                                                |
| unpause   | Unpause the cluster                                                  |

Images:
| Command    | Description                                                           |
| ---------- | --------------------------------------------------------------------- |
| docker-env | Instructions to point docker-cli to the Docker Engine inside minikube |
| podman-env | Configure environment to use minikube's Podman service                |
| cache      | Manage cache for images                                               |
| image      | Manage images                                                         |

Configuration and Management Commands:
| Command        | Description                                 |
| -------------- | ------------------------------------------- |
| addons         | Enable/disable a minikube addon             |
| config         | Modify persistent config values             |
| profile        | Get or list current profiles (clusters)     |
| update-context | Update kubeconfig in case of IP/port change |

Networking and Connectivity Commands:
| Command | Description                           |
| ------- | ------------------------------------- |
| service | Returns a URL to connect to a service |
| tunnel  | Connect to Load Balancer services     |

Advanced Commands:
| Command | Description                                       |
| ------- | ------------------------------------------------- |
| mount   | Mounts the directory into minikube                |
| ssh     | Log into the minikube env for debugging           |
| kubectl | Run a kubectl binary matching the cluster version |
| node    | Add/Remove/List nodes                             |
| cp      | Copy the file into minikube                       |

Troubleshooting Commands:
| Command      | Description                               |
| ------------ | ----------------------------------------- |
| ssh-key      | Show SSH ID key path of a node            |
| ssh-host     | Show SSH host key of a node               |
| ip           | Show the IP address of a node             |
| logs         | Returns logs to debug a local K8S cluster |
| update-check | Print current/latest version numbers      |
| version      | Print minikube version                    |
| options      | Show list of global CLI options           |

Other Commands:
| Command    | Description                                     |
| ---------- | ----------------------------------------------- |
| completion | Generate command completion for a shell         |
| license    | Outputs licenses of dependencies to a directory |




