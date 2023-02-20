
```toc
```

## Installation

### Compiling from Source
```bash
$ mkdir -p $(go env GOPATH)/src/github.com/hashicorp && cd $_
$ git clone https://github.com/hashicorp/packer.git
$ cd packer
$ make dev
```

### Pre-Compiled Binaries
[Download Here](https://packer.io/downloads.html) 

#### OS X
Use Homebrew
```bash
$ brew tap hashicorp/tap
$ brew install hashicorp/tap/packer
# to Upgrade:
$ brew upgrade hashicorp/tap/packer
```

#### Windows
Use Chocolatey
```bash
$ choco install packer
```

#### Linux

##### Ubuntu/Debian
Install package `packer` from [apt repo](https://apt.releases.hashicorp.com) - [GPG Key](https://apt.releases.hashicorp.com/gpg).

##### RHEL/CentOS
Use Hashicorp's prepared [Repository File](https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo)
Install package `packer`

### Verifying the Installation
```bash
$ packer --version
```

## Usage

### Initialize a new Project
```
packer init .
```
Reads the packer block and downloads needed plugins.
- Set `PACKER_GITHUB_API_TOKEN` to get around GitHub download rate limiting.
- Use `packer init -upgrade` to get latest versions of all plugins

### Formatting and Validation
```
packer fmt .
packer validate .
```
Formats and validates packer templates

### Building Images from Packer Templates
```
packer build my-build.pkr.hcl
```
- `-color=false` turns off colorized output
- `-debug` turns on additional logging and disables parallelization
- `-except=foo,bar,baz` - Runs all builds and post-processors except those named
- `-force` - Force a builder to run even when artifacts already exist.
- `-on-error=(cleanup|abort|ask|run-cleanup-provisioner)` - Selects what to do when build fails during provisioning
	- `cleanup` deletes temporary files and virtual machines
	- `abort` exist without cleanup
	- `ask` prompts to clean up, abort, or retry
	- `run-cleanup-provisioner` aborts with no cleanup but runs the `error-cleanup-provisioner` if defined
- `-only=foo,bar,baz` - Runs *only* the named builds
- `-parallel-builds=N` - Limits number of builds to run in parallel. 0 (default) means no limit.
- `-timestamp-ui` - Prefixes each UI output with RFC3339 timestamp
- `-var "foo=bar"` - Sets variable for build. Can be used multiple times.
- `-var-file=foo.pkrvars.hcl` - Sets variables from a file

## Templates
Main configuration file defining what and how to build the image.
Written in HCL2 (preferred, `.pkr.hcl`) or JSON (deprecated, `.pkr.json`).
Consists of packer, source, and build blocks (order not significant)

### Packer Block
```HCL
packer {
	required_plugins {
		docker = {
			version = ">= 0.0.7"
			source = "github.com/hashicorp/docker"
		}
	}
}
```
- Contains packer settings
- Can specify a required packer version
- `required_plugins` block
	- specifies plugins needed
	- optionally specifies version range needed
	- optionally specifies source if outside of HashiCorp domain

### Source Block
```hcl
source "docker" "ubuntu" {
  image  = "ubuntu:xenial"
  commit = true
}
```
- Builder plugin is immediately after "source" statement ("docker" here).
- Name of source block is after builder plugin ("ubuntu")
- Attributes inside are determined by the plugin used
- Specifies *communicators* (ssh, WinRM, e.g.) for communicating with image

### Build Block

```hcl
build {
  name    = "learn-packer"
  sources = [
    "source.docker.ubuntu"
  ]
}
```
- Define what packer should do with the container/VM after it launches
- Can contain Provisioner blocks and Post-Processor Blocks to add additional steps

#### Provisioner Block
```HCL
provisioner "shell" {
	only = ["amazon-ebs.first-example"]
	inline = [
	  "echo provisioning all of the things",
	  "echo the value of 'foo' is '${var.foo}'",
	]
}
```

Provisioners provide steps to perform after the VM/container is live and installed.
`only` and `except` specify which Build Blocks to run against.

##### Provisioners
Breakpoint, file, PowerShell, Shell, Shell (Local), Windows Shell, Windows Restart, Custom, Comment (Community supported), Windows Update (Community Supported)

You can also define an error provisioner to run in the event of a build failure.

##### Post-Processor Block
Packer Post-processors run after the image is built and provisioners are run.
They can be used to upload artifacts, repackage, etc.


---
# Resources
[Documentation | Packer by HashiCorp](https://www.packer.io/docs)
[Terminology | Packer by HashiCorp](https://www.packer.io/docs/terminology)
[Provision Infrastructure with Packer | Terraform - HashiCorp Learn](https://learn.hashicorp.com/tutorials/terraform/packer)
[Packer Examples for vSphere - GitHub](https://github.com/rainpole/packer-vsphere)
