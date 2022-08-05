---
attachments: [Clipboard_2022-07-15-20-57-12.png, Clipboard_2022-07-15-21-03-17.png]
tags: [Notebooks/Github]
title: SSH
created: '2022-07-15T12:54:02.320Z'
modified: '2022-07-19T12:50:30.894Z'
---

# SSH

### generating SSH keys
```bash
ssh-keygen -t ed25519 -C "james.a.esguerra@obf.ateneo.edu"
```

### rename dir
```bash
/home/james/.ssh/
```

### start ssh agent
```bash
eval "$(ssh-agent -s)"
```

### add key to agent
```bash
ssh-add ~/.ssh/id_ed25519
```

### copy key to clipboard
```bash
cat ~/.ssh/id_ed25519.pub
```

### add to Github account
go to Profile > SSH keys

### switch to ssh protocol in git
```bash
git remote -v
git remote remove origin
git remote add origin git@github.com:user/repo.git
```
