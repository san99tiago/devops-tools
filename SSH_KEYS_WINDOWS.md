# Configure SSH Keys for GitHub: Windows Steps

LINKS:

- https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
- https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

GIT-BASH:

```bash
# Move to the SSH keys folder
cd ~/.ssh

# Create the Key
ssh-keygen -t ed25519 -C "san99tiago@gmail.com GitHub" -f id_ed25519
```

POWERSHELL:

```powershell
# Enable the configurations and start the agent
Get-Service -Name ssh-agent | Set-Service -StartupType Manual
ssh-agent start

# Add the SSH keys
ssh-add.exe C:\Users\santi\.ssh\id_ed25519

# It should say...
# Identity added: C:\Users\santi\.ssh\id_ed25519(san99tiago@gmail.com GitHub)
```

GITHUB:

```bash
# 1) Copy the public key... (the "github_demo.pub" content)

# 2) Go to GitHub in "Profile" --> "Settings" --> "SSH Keys" --> "Add key"
```

# Troubleshooting Windows

```bash
# Remove specific SSH Key
ssh-add -d C:\Users\santi\.ssh\id_ed25519

# Remove all existing SSH Keys
ssh-add -D

# Check connectivity to the correct domain
ssh -vT git@github.com

```

```bash
# IMPORTANT
# --> If the key is named different, if might cause issues and ...
# --> ... we would have to create/configure the "~/.ssh/config"  file
```
