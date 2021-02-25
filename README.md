# GPG Notes:

### Start GPG Agent:
```
gpg-agent --daemon
export GPG_TTY=$(tty)
```

### List keys:
```
gpg --list-keys
```

### Generate keys:
```
gpg --full-generate-key
```
Recommended setting: default (1), keysize 4096

### Edit key:
```
gpg --edit-key t3hami@gmail.com
```
Now you can use following commands in interactive GPG console:
```
key 0
expire
adduid
revuid
save
```

### Change passphrase:
```
gpg --passwd t3hami@gmail.com
```

### Export public key:
```
gpg --export --armor t3hami@gmail.com
gpg --export --armor --output t3hami.gpg.pub t3hami@gmail.com
```

### Import public key:
```
gpg --import t3hami.gpg.pub
```

### Export public key to server (By default: https://hkps.pool.sks-keyservers.net:443):
```
gpg --list-keys --keyid-format LONG t3hami@gmail.com
gpg --send-keys 6CCDC54DB29B4E9C
```

### Import public key from server:
```
gpg --search-keys t3hami@gmail.com
gpg --recv-keys 6CCDC54DB29B4E9C
```

### Export private key:
```
gpg --export-secret-keys t3hami@gmail.com > private.key
```

### Import private key:
```
gpg --import private.key
```

### Delete public key:
```
gpg --delete-keys t3hami@gmail.com
```

### Delete private key:
```
gpg --delete-secret-keys t3hami@gmail.com
```

### Default TTL for passphrase, file ~/.gnupg/gpg-agent.conf:
```
default-cache-ttl 86400
max-cache-ttl 86400
```

### Signing commits:
```
git commit -S -m "commit message"
git log --show-signature
```

### Signing tags:
```
git tag -sm "release message with signed tag" v1.3
```

### Verifying commits:
```
git merge --verify-signature feature-branch
```

### Other useful git commands:
```
git tag v1.0
git tag -a v1.1 -m "release message"
git tag

git show v1.1

git push origin v1.0
git push origin --tags
git push --tags

git tag -am "release message" v1.2

git tag v1.3 -v
```

### References:
- https://www.youtube.com/watch?v=1vVIpIvboSg
- https://redmine.dicelab.net/projects/instructibels/wiki/Adding_Secondary_Email_Addresses_to_GPG_Keys (Adding multiple emails in single GPG key)
- https://makandracards.com/makandra-orga/37763-gpg-extract-private-key-and-import-on-different-machine
- https://www.youtube.com/watch?v=4166ExAnxmo&t=1s
- https://access.redhat.com/solutions/2115511 (Import all keys to new machine)

