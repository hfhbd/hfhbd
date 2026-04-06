# Generate A Non Exportable SSH Key for Git Signing

```shell
sc_auth create-ctk-identity -l GitHub -k p-256-ne -t bio -E id+username@users.noreply.github.com
ssh-add -K -S /usr/lib/ssh-keychain.dylib
ssh-add -L
ssh-copy-id git@github.com
ssh -o SecurityKeyProvider=/usr/lib/ssh-keychain.dylib git@github.com
```
Upload the key to GitHub via the UI


To add the key locally for git
```shell
ssh-keygen -w /usr/lib/ssh-keychain.dylib -K -N ""
echo "$(git config --get user.email) namespaces=\"git\" $(cat ~/.ssh/id_github.pub)" >> ~/.ssh/allowed_signers
```
