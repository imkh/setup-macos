# setup-macos

Personal setup for a new macOS install.

## Install the Xcode Command Line Tools

```sh
$ xcode-select -p # Check if the full Xcode package is already installed
$ xcode-select --install # Install Xcode Command Line Tools
```

## Install Homebrew

```sh
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## Install Node.js and npm

```sh
$ brew install node
```

## Install and set up Zsh

More information on this [wiki page from Oh-My-Zsh](https://github.com/robbyrussell/oh-my-zsh/wiki/Installing-ZSH) and this [gist](https://gist.github.com/kevin-smets/8568070).

### Check if zsh is already installed

```sh
$ zsh --version # If installed, should be zsh 5.0 or more recent
$ echo $SHELL # Expected result should be usr/bin/zsh or /bin/zsh
```

### Install zsh and make it the default shell

```sh
$ brew install zsh zsh-completions # Install zsh
$ zsh --version # Should be zsh 5.0 or more recent
$ chsh -s $(which zsh) # Make zsh the default shell
$ echo $SHELL # Expected result should be usr/bin/zsh or /bin/zsh
```

### Install Oh-My-Zsh

```sh
$ sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

### Set personal custom theme & prompt

```sh
$ curl https://gist.githubusercontent.com/imkh/db581924555a3a69f6be658a4c42d7bb/raw/d38d501bd9c9e60299d8fd96ac075873a8eacf44/refined-imkh --create-dirs -o $ZSH_CUSTOM/themes/refined-imkh.zsh-theme
```

And in `~/.zshrc`:

```
ZSH_THEME="refined-imkh"
```

### Add zsh-autosuggestions

```sh
$ git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

And add `zsh-autosuggestions` as a plugin in `~/.zshrc`, like this:

```
plugins=(
  git zsh-autosuggestions
)
```

### Add syntax highlighting

```sh
$ brew install zsh-syntax-highlighting
```

And add this to the end of the `~/.zshrc` file:

```
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

## Essential Apps

| Name | Description | Paid? | Settings |
| ---------------- | ------------- |:-----:|:--------:|
| [1Password](https://1password.com/) | Password manager. | 💰 | [Yes](./settings/1password) |
| [Google Chrome](https://www.google.com/chrome/) | Web browser.  |   | [Yes](./chrome/1password) |
| [Microsoft Office](https://www.office.com) | Office productivity suite. |   |   |
| [Slack](https://www.slack.com) | Team communication app. |   |   |
| [Firefox Developer Edition](https://www.mozilla.org/en-US/firefox/developer/) | Web browser. |   |   |
| [Spark](https://itunes.apple.com/us/app/spark-love-your-email-again/id1176895641?mt=12) | Email desktop client. |   | [Yes](./settings/spark) |
| [Fantastical 2](https://flexibits.com/fantastical) | Calendar desktop client. | 💰 | [Yes](./settings/fantastical2) |
| [Magnet](https://itunes.apple.com/us/app/magnet/id441258766?mt=12) | Window manager. | 💰 |   |
| [Google Play Music Desktop Player](https://www.googleplaymusicdesktopplayer.com/) | Google Play Music desktop client. |   | [Yes](./settings/gpmdp) |
| [OneDrive](https://itunes.apple.com/us/app/onedrive/id823766827?mt=12) | OneDrive syncing. |   |   |
| [Google Backup and Sync](https://www.google.com/drive/download/backup-and-sync/) | Google Drive syncing. |   |   |

## Development Tools

| Name | Description | Paid? | Settings |
| ---------------- | ------------- |:-----:|:--------:|
| [Tower](https://www.git-tower.com/) | Git desktop client. | 💰 | [Yes](./settings/tower) |
| [Kaleidoscope](https://www.kaleidoscopeapp.com/) | File comparison app (diff tool). | 💰 |  |
| [Paw](https://paw.cloud/) | Full-featured HTTP client for API development (similar to Postman). | 💰 | [Yes](./settings/paw) |
| [iTerm2](https://www.iterm2.com/) | Terminal emulator for macOS. | | [Yes](./settings/iterm2) |
| [Hyper](http://hyper.is/) | JS/HTML/CSS Terminal. | | [Yes](./settings/hyper) |
| [Visual Studio Code](https://code.visualstudio.com/) | Source code editor. | | [Yes](./settings/vscode) |
| [Sublime Text](https://www.sublimetext.com/) | Source code editor. | | [Yes](./settings/sublime) |
| [Xcode](https://itunes.apple.com/fr/app/xcode/id497799835?l=en&mt=12) | Official IDE for macOS, iOS, watchOS, and tvOS development. | | |
| [Android Studio](https://developer.android.com/studio/index.html) | Official IDE for Android development. | | [Yes](./settings/androidstudio) |
| [Docker](https://www.docker.com/) | Create, deploy, and run applications by using containers. | | [Yes](./settings/docker) |
| [Sequel Pro](https://www.sequelpro.com/) | MySQL database management tool. | 💰 | |
| [Robo 3T](https://robomongo.org/) | MongoDB database management tool. | | |
| [DB Browser for SQLite](http://sqlitebrowser.org/) | SQLite database management tool. | | |

## Useful Apps

| Name | Description | Paid? | Settings |
| ---------------- | ------------- |:-----:|:--------:|
| [Cisco Spark](https://www.ciscospark.com/) | Team messaging app. | | |
| [VLC](https://www.videolan.org/vlc/index.html) | Multimedia player. | | |
| [Tweetbot](https://itunes.apple.com/us/app/tweetbot-for-twitter/id557168941?mt=12) | Twitter desktop client. | 💰 | |
| [Skype](https://www.skype.com/en/) | Voice & text chat app. | | |
| [Discord](https://discordapp.com/) | Voice & text chat app for gaming communities. | | |
| [Reflector](http://www.airsquirrels.com/reflector/) | Android & iOS wireless screen mirroring. | 💰 | |
| [Tuxera](https://www.tuxera.com/products/tuxera-ntfs-for-mac/) | NTFS drives read and write support. | 💰 | |
| [Gifox](https://gifox.io/) | GIF recording and sharing. | 💰 | |
| [TunnelBear](https://www.tunnelbear.com/) | Secure VPN service. | 💰 | |
| [Sip](https://sipapp.io/)  | Color picker for macOS. | 💰 | [Yes](./settings/sip) |
| [TeamViewer](https://www.teamviewer.com/en/) | Remote control tool. | | |

## Gaming Apps

| Name | Description | Paid? | Settings |
| ---------------- | ------------- |:-----:|:--------:|
| [Steam](http://store.steampowered.com/) | Gaming digital distribution platform. | | |
| [PS4 Remote Play](https://remoteplay.dl.playstation.net/remoteplay/lang/en/index.html) | Remote play for PlayStation 4. | | |

## Other

| Name | Description | Paid? | Settings |
| ---------------- | ------------- |:-----:|:--------:|
| [Adobe Photoshop](https://www.adobe.com/products/photoshop.html) | Photo, image and design editing tool. | 💰 |  |
| [Sketch](https://www.sketchapp.com/) | Digital design toolkit. | 💰 |  |
| [Parallels](https://www.parallels.com/) | Mac & Windows virtualization. | 💰 |  |
| [Cornerstone](https://cornerstone.assembla.com/) | SVN client for macOS. | 💰 |  |
| [The Archive Browser](https://theunarchiver.com/archive-browser) | Browser for archive type files (zip, rar, 7-zip, tar, etc). | 💰 |  |
| [Texpad](https://www.texpad.com/) | LaTeX editor. | 💰 |  |

## Git global configuration

### gitignore

```sh
$ curl https://raw.githubusercontent.com/github/gitignore/master/Global/macOS.gitignore -o ~/.gitignore_global
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