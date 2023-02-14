Encryption at the file or YAML line-item level, for example to store secrets in a file.

## Encryption

Usage: `ansible-vault OPERATION ARGUMENTS`

Output an encrypted string:
- `ansible-vault encrypt_string 'SuperSecretPassphrase'`
Replace a file with an encrypted version:
- `ansible-vault encrypt myfile.yml`

Password can be supplied with
- `--ask-vault-password`
- `--vault-password-file FILE`
- `--vault-id VAULT_ID`

Sample output:
```
!vault |
        $ANSIBLE_VAULT;1.1;AES256
        34623039373638383361333733623036663031333337333861363632623932633833613736386266
        6637636161396434336265636563323364386439323531340a643665393836633363623963353565
        [...]
```

| Operation      | Description                     |
| -------------- | ------------------------------- |
| create         | Create new vault encrypted file |
| decrypt        | Decrypt vault encrypted file    |
| edit           | Edit vault encrypted file       |
| view           | View vault encrypted file       |
| encrypt        | Encrypt YAML file               |
| encrypt_string | Encrypt a string                |
| rekey          | Re-key a vault encrypted file   |

