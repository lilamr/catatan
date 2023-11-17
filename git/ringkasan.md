install git
`sudo apt install git-all`

masukan user dan email
`git config --global user.name "Your Name Here"`
`git config --global user.email "your_email@example.com"`

buat dan masuk ke folder
`cd Documents`
`mkdir HaloWhirled`
`cd HaloWhirled`

Aktifkan git pada folder
`git init`

Buat dan tambahkan file ke git
`touch TheFirstFile.txt`
`git add TheFirstFile.txt`

Simpan perubahan file secara lokal
`git commit -am "Initial Commit"`

Simpan perubahan di github
`git push`

Ambil perubahan dari github
`git pull`


===========================



This summary of basic Git commands should be handy as a reference while you explore and learn more:

Tell Git what files to track for changes
`git add <filename, folder name or list of filenames (separated by spaces)>`

Store the current state so you can always return to it
`git commit -am “A message that will help you understand what this commit contains”`

To restore all the files from a previous commit
`git checkout <an unambiguous portion of the hash>`

To get the hashes of previous commits
`git log`

To interact with “remote” git repositories (such as projects on Github)
`git push`
`git pull`
