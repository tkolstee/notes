
```toc
```

## Retrieve a Single file from a Revision
[source](https://stackoverflow.com/questions/610208/how-to-retrieve-a-single-file-from-a-specific-revision-in-git)

```
git show $REV:$FILE
git show somebranch:from/the/root/myfile.txt
git show HEAD^^^:test/test.py
```
`$REV` can be (the first few characters of) a SHA1 commit hash
`HEAD^^^` indicates how many commits prior to HEAD should be used

## Remote Git Repository via SSH
[Source](https://git-scm.com/book/en/v2/Git-on-the-Server-Setting-Up-the-Server)

**Set up the server**
- Create a user account and .ssh directory
- Add SSH public keys to authorized_keys

**Set up the project**
- On server, create a new project directory and run `git init --bare` inside it
- On client, run `git remote add origin user@server:/path/to/project.git` in your project
You can now upload the project to the server with `git push` commands

**Clone the project:**
- git clone user@server:/path/to/project.git

**Restricting server users:**
- Add the full path of `git-shell` to `/etc/shells`
- Make `git-shell` the git user's default shell
- Prepend to keys (before `ssh-rsa`) in git user's `authorized_keys` file:
```
no-port-forwarding,no-X11-forwarding,no-agent-forwarding,no-pty
```

## Hints

### CRLF and Windows
Windows will translate files to CRLF if using git in default mode.
To keep files in their existing mode: `git config --global core.autocrlf false`