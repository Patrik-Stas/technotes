# Technotes

## Ubuntu 16 / NPM
#### Installing global packages as non-root
If you install Node and NPM which Ubuntu ships by default, you won't be able to install 
global npm packages without `sudo`. You can try to remedy this issue by setting up
npm to install global packages only in scope of current user, not the whole system.
For that, you could follow this:
https://stackoverflow.com/questions/18088372/how-to-npm-install-global-not-as-root
- **But!** Easier way is simply first install `NVM` which seems too already be handling 
this problem and `npm install -g` work without sudo out of the box.

## Ubuntu 18
### Securing instance with root-only access
In cases where the only accessible user is root, such as it happens to be on 
Digital Ocean images by default, we need to create new sudo user and revoke 
direct SSH access to root.
- Create new user: `adduser ubuntu`
- Add the user to group `sudo`: `usermod -aG sudo ubuntu`
- Switch current user `su ubuntu`
- `cd ~`
- `mkdir -p .ssh; touch .ssh/authorized_keys;`
- Copy authorized keys from root `sudo cat /root/.ssh/authorized_keys >> ~/.ssh/authorized_keys`
- Revoke SSH access to root user, open fil `sudo vi /etc/ssh/sshd_config` and change `PermitRootLogin yes` to `PermitRootLogin no`
- Restart SSH daemon service `sudo service ssh restart`
- Check status `sudo service ssh status`
- Before you disconnect yourself from current SSH session, make sure you are able to SSH into `ubuntu` user.
