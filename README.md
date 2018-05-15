# dotfiles
dotfiles to add kun-fu power to command line 

- styling prompt -> .bash_prompt
- creating aliases -> .aliases
- exporting variables -> .exports

# Paste into bash_profile
```bash
# Load the shell dotfiles, and then some:
for file in ~/.dotfiles/.{bash_prompt,exports,aliases}; do
	[ -r "$file" ] && [ -f "$file" ] && source "$file";
done;
unset file;

# Add tab completion for SSH hostnames based on ~/.ssh/config, ignoring wildcards
[ -e "$HOME/.ssh/config" ] && complete -o "default" -o "nospace" -W "$(grep "^Host" ~/.ssh/config | grep -v "[?*]" | cut -d " " -f2- | tr ' ' '\n')" scp sftp ssh;

source ~/.dotfiles/iterm2/helpers.sh
```
