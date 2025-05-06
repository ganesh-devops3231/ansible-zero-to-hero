# How to setup Passwordless Authentication

## EC2 Instances

### Using Public Key

```
ssh-copy-id -f "-o IdentityFile <PATH TO PEM FILE>" ubuntu@<INSTANCE-PUBLIC-IP>
```

- ssh-copy-id: This is the command used to copy your public key to a remote machine.
- -f: This flag forces the copying of keys, which can be useful if you have keys already set up and want to overwrite them.
- "-o IdentityFile <PATH TO PEM FILE>": This option specifies the identity file (private key) to use for the connection. The -o flag passes this option to the underlying ssh command.
- ubuntu@<INSTANCE-IP>: This is the username (ubuntu) and the IP address of the remote server you want to access.

### Using Password 

- Go to the file `/etc/ssh/sshd_config.d/60-cloudimg-settings.conf`
- Update `PasswordAuthentication yes`
- Restart SSH -> `sudo systemctl restart ssh`

### Using ssh key
- Using ```ssh-keygen```, It will creates a folder called .ssh with a private key and public key.
- Now go to target VM created, and do the same process like above but no need to copy the public key.
- Go to ansible control VM, and use command ```sudo-copy-id <target-username>@<target-IP>```. This will ask for password and then it will create the authorized_keys file with public key of ansible sourced VM and paste there.
- Now in target VM, give permissions like
  ```
	chmod 600 ~/.ssh
  ```
  ```
	chmod 700 ~/.ssh/authorized_key
  ```
- Now in ansible control VM, in ansible folder create a file name as inventory. In that write like 
	-- targetIP ansible-user=targetVMusername
- And finally give command for ansible adhoc command as:
  ```
	ansible -i inventory all -m shell -a "touch firstfile"
  ```

Errors: There was unreachable between sourced vm and target vm this is because of inventory file doesn't contain the ansible-user and because of this it is trying to connect with source vm username.
