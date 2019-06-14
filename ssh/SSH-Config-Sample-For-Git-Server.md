

### SSH Config Sample For Git Server

```
Host bitbucket.org
  HostName bitbucket.org
  IdentityFile ~/.ssh/id_rsa
#    ForwardX11Trusted yes
  StrictHostKeyChecking no
  UserKnownHostsFile /dev/null
  User git
  LogLevel QUIET

```
