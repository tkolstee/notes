Client will use all keys under `~/.ssh` or SSH-agent

```python
from pssh.clients import ParallelSSHClient
client = ParallelSSHClient( list_of_hostnames )

# Multiple clients
output = client.run_command('uname -a')


for host_out in output:
	for line in host_out.stdout:
		print(line)
	exit_code = host_out.exit_code

# Single host client
client = SSHClient('localhost')
host_out = client.run_command('uname')
for line in host_out.stdout:
    print(line)
exit_code = host_out.exit_code
```

`output` is a list of `host_out` objects