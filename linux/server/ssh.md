# Harden ssh

```sh
sudoedit /etc/ssh/sshd_config
```

Make ssh more secure by enable below settings:

```config
-- disable root login
#PermitRootLogin prohibit-password
-- limit how many times to fail
MaxAuthTries 6
-- limit how many sessions at the same time
MaxSessions 5
-- only use pubkey to auth
PubkeyAuthentication yes
-- clean up old sessions
TCPKeepAlive yes
```

Reload `sshd` daemon

```sh
sudo systemctl reload sshd
```
