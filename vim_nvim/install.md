Install vim:
`sudo apt install vim`

Install neovim (nvim):
`cd /opt`
`sudo mkdir nvim`
`cd nvim`

`sudo curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim.appimage`
`sudo chmod u+x nvim.appimage`
`sudo ./nvim.appimage`

Exposing nvim globally:
`sudo ./nvim.appimage --appimage-extract`
`sudo ./squashfs-root/AppRun --version`

`sudo mv squashfs-root /`
`sudo ln -s /squashfs-root/AppRun /usr/bin/nvim`
`nvim`
