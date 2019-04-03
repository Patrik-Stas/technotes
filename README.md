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
