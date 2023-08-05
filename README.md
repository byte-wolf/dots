# dots

This is my personal configuration currently under void linux. 

## Nushell

```bash
sudo xbps-install nushell
chsh -s /usr/bin/nu USERNAME
nu
```

```nushell
echo "let-env EDITOR = vim" | save -a $nu.env-path
```


### Aliases

```nushell
echo "alias ll = ls -al" | save -a $nu.config-path
```

## Pulse Audio
