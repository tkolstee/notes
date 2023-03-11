## Add the GPG Key

`apt-key` is deprecated, because it trusts ANY packages signed with that key regardless of repository.

Some solutions will propose adding individual files to `/etc/apt/trusted.gpg/` but this leads to the same problem as the above.

This shell function takes the name of the repo and the URL of the key, e.g.:

> `add_key docker 'https://download.docker.com/linux/debian/gpg'`

```bash
add_key() {
  reponame=$1
  keyurl=$2
  [ -d /etc/apt/keyrings ] || mkdir -p /etc/apt/keyrings
  keyfile=$(mktemp)
  keyring=$(mktemp)
  wget -O "${keyfile}" "${keyurl}"
  gpg --no-default-keyring --keyring "${keyring}" --import "${keyfile}"
  gpg --no-default-keyring --keyring "${keyring}" --export --output "/etc/apt/keyrings/${reponame}.gpg"
  rm -f "${keyfile}" "${keyring}"
}
```

The key is imported and reexported through GPG using a temporary keyring to canonicalize it, as the original may be in various formats. This replaces the `gpg --dearmor --yes -o outfile` step required by many similar suggestions.

The final key is placed into `/etc/apt/keyrings/${reponame}.gpg`.

## Add the Repository
Create a file in `/etc/apt/sources.list.d/${reponame}.list`.

Example:
`deb [arch=amd64 signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian bullseye stable`

----
# Sources
[Adding apt keys](https://askubuntu.com/questions/1286545/what-commands-exactly-should-replace-the-deprecated-apt-key)
