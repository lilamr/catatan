Try the following commands, one after another. If you progress, respective folders may already be deleted:

1. `sudo apt-get purge texlive*`
    
2. `sudo rm -rf /usr/local/texlive/*` and `rm -rf ~/.texlive*`
    
3. `sudo rm -rf /usr/local/share/texmf`
    
4. `sudo rm -rf /var/lib/texmf`
    
5. `sudo rm -rf /etc/texmf`
    
6. `sudo apt-get remove tex-common --purge`
    
7. `rm -rf ~/.texlive`
    
8. `find -L /usr/local/bin/ -lname /usr/local/texlive/*/bin/* | xargs -r rm`

This finds all the files in `/usr/local/bin` which point to a location within `/usr/local/texlive/*/bin/*` and removes them; because we’ve already deleted all of `/usr/local/texlive`, these are dead links. To see which files are being deleted, replace `xargs rm` with `xargs -t rm` (or `tee` off to a log file, or whatever).

### Update

In case that - after the last command (8.) - your terminal returns something like this

```latex
rm: cannot remove '/usr/local/bin/deweb': Permission denied
rm: cannot remove '/usr/local/bin/dviconcat': Permission denied
rm: cannot remove '/usr/local/bin/pkfix-helper': Permission denied
rm: cannot remove '/usr/local/bin/ulqda': Permission denied
rm: cannot remove '/usr/local/bin/kpsereadlink': Permission denied
rm: cannot remove '/usr/local/bin/bibmradd': Permission denied
...
...
...
```

if you know what you're doing, you can add `sudo` between the pipe and `xargs rm`, so that it becomes

```latex
find -L /usr/local/bin/ -lname /usr/local/texlive/*/bin/* | sudo xargs rm
```

or, to be more careful and also more thorough, follow the steps of [this answer](https://tex.stackexchange.com/a/257042/117274), which worked for [me](https://tex.stackexchange.com/users/117274/thymaro).

### Update 2

Refer to [this answer](https://stackoverflow.com/a/36618260.) to solve the issue of `rm: missing operand` when running (8.)