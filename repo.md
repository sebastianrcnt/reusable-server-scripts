## Option 1: Use Github CLI
1. install gh cli
```sh
(type -p wget >/dev/null || (sudo apt update && sudo apt-get install wget -y)) \
&& sudo mkdir -p -m 755 /etc/apt/keyrings \
&& wget -qO- https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null \
&& sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y
```

### add to ssh aliases
```ssh-config
Host github.com-[repo-alias]
	Hostname github.com
	IdentityFile /home/ubuntu/.ssh/[public-key-file]
```

### remove and add origin again
```sh
git remote -v
git remote remove origin
git remote add origin git@github.com-[repo-alias]:[owner]/[repo].git
```
