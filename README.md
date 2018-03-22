# setup-macos

Personal setup for a new macOS install.

## Install the Xcode Command Line Tools

```sh
$ xcode-select -p # Check if the full Xcode package is already installed
$ xcode-select --install # Install Xcode Command Line Tools
```

## Essential Apps

* [1Password](https://1password.com/) 💰
* [Google Chrome](https://www.google.com/chrome/)
* [Microsoft Office](https://www.office.com)
* [Slack](https://www.slack.com)
* [Firefox Developer Edition](https://www.mozilla.org/en-US/firefox/developer/)
* [Spark](https://itunes.apple.com/us/app/spark-love-your-email-again/id1176895641?mt=12)
* [Fantastical 2](https://flexibits.com/fantastical) 💰
* [Magnet](https://itunes.apple.com/us/app/magnet/id441258766?mt=12) 💰
* [Google Play Music Desktop Player](https://www.googleplaymusicdesktopplayer.com/)
* [OneDrive](https://itunes.apple.com/us/app/onedrive/id823766827?mt=12)
* [Google Backup and Sync](https://www.google.com/drive/download/backup-and-sync/)

## Development Tools

* [Tower](https://www.git-tower.com/) 💰
* [Paw](https://paw.cloud/) 💰
* [iTerm2](https://www.iterm2.com/)
* [Hyper](http://hyper.is/)
* [Visual Studio Code](https://code.visualstudio.com/)
* [Sublime Text](https://www.sublimetext.com/)
* [Xcode](https://itunes.apple.com/fr/app/xcode/id497799835?l=en&mt=12)
* [Android Studio](https://developer.android.com/studio/index.html)
* [Docker](https://www.docker.com/)
* [Sequel Pro](https://www.sequelpro.com/) 💰
* [Robo 3T](https://robomongo.org/)
* [DB Browser for SQLite](http://sqlitebrowser.org/)

## Useful Apps

* [Cisco Spark](https://www.ciscospark.com/)
* [VLC](https://www.videolan.org/vlc/index.html)
* [Tweetbot](https://itunes.apple.com/us/app/tweetbot-for-twitter/id557168941?mt=12) 💰
* [Skype](https://www.skype.com/en/)
* [Discord](https://discordapp.com/)
* [Reflector](http://www.airsquirrels.com/reflector/) 💰
* [Tuxera](https://www.tuxera.com/products/tuxera-ntfs-for-mac/) 💰
* [Gifox](https://gifox.io/) 💰
* [TunnelBear](https://www.tunnelbear.com/) 💰
* [Sip](https://sipapp.io/) 💰
* [TeamViewer](https://www.teamviewer.com/en/)

## Games

* [Steam](http://store.steampowered.com/)
* [PS4 Remote Play](https://remoteplay.dl.playstation.net/remoteplay/lang/en/index.html)

## Other

* [Adobe Photoshop](https://www.adobe.com/products/photoshop.html) 💰
* [Sketch](https://www.sketchapp.com/) 💰
* [Kaleidoscope](https://www.kaleidoscopeapp.com/) 💰
* [Parallels](https://www.parallels.com/) 💰
* [Cornerstone](https://cornerstone.assembla.com/) 💰
* [The Archive Browser](https://theunarchiver.com/archive-browser) 💰
* [Texpad](https://www.texpad.com/) 💰

## Git global configuration

### gitignore

```sh
$ echo ".DS_Store" >> ~/.gitignore_global
```

### gitconfig

Create a git config file:

```sh
$ touch ~/.gitconfig
```

And write in it:

```
[user]
        name = <Full Name>
        email = <Email Address>
[core]
        excludesfile = ~/.gitignore_global
        editor = <emacs -ne || subl -w || slap>
```

## Set up Git SSH Keys

### Official documentation

* [GitHub](https://help.github.com/articles/connecting-to-github-with-ssh/)
* [GitLab](https://docs.gitlab.com/ee/ssh/README.html)

### Initial configuration

Create a SSH config file:

```sh
$ touch ~/.ssh/config
```

And write in it:

```
# GitHub.com server
Host github.com
 AddKeysToAgent yes
 UseKeychain yes
 IdentityFile ~/.ssh/id_rsa

# Private Enterprise GitLab server
Host <gitlab.company.com>
 RSAAuthentication yes
 IdentityFile ~/.ssh/id_rsa_gitlab_<company_name>
```

### Generate and add SSH keys

```sh
$ ls -al ~/.ssh # Lists the files in your .ssh directory, if they exist
$ ssh-keygen -t rsa -b 4096 -C "email@domain.com" # Generate a new SSH key
$ pbcopy < ~/.ssh/id_rsa.pub # Copies the contents of the id_rsa.pub file to your clipboard
```

Then paste the content of the clipboard in:
* `Settings > SSH and GPG keys > New SSH key` for [*GitHub*](https://github.com/settings/ssh/new).
* `Settings > SSH Keys > New SSH key` for *GitLab*.