### SSH copy from win
```
type $env:USERPROFILE\.ssh\id_rsa.pub | ssh {IP-ADDRESS-OR-FQDN} "cat >> .ssh/authorized_keys"
```
### Permissions
```
chmod go-w /home/user
chmod 700 /home/user/.ssh
chmod 600 /home/user/.ssh/authorized_keys
```
### keygen SSH keys
```
ssh-keygen -t rsa -b 4096 -C "mail@mail.com"
```