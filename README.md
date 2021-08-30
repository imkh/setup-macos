# setup-macos

Personal setup for a new macOS install.

## Table of Contents

- [Install the Xcode Command Line Tools](#install-the-xcode-command-line-tools)
- [Install Homebrew](#install-homebrew)
- [Install and set up Zsh](#install-and-set-up-zsh)
  - [Check if zsh is already installed](#check-if-zsh-is-already-installed)
  - [Install zsh and make it the default shell](#install-zsh-and-make-it-the-default-shell)
  - [Install Oh-My-Zsh](#install-oh-my-zsh)
  - [Set personal custom theme & prompt](#set-personal-custom-theme--prompt)
  - [Add syntax highlighting](#add-syntax-highlighting)
  - [Set window & tab title to current directory](#set-window--tab-title-to-current-directory)
- [Install GNU ls for better ls colors](#install-gnu-ls-for-better-ls-colors)
- [Install Emacs](#install-emacs)
- [Install Go](#install-go)
- [Install Node.js and npm](#install-nodejs-and-npm)
- [Install MySQL](#install-mysql)
- [Install PostgreSQL](#install-postgresql)
- [Install MongoDB](#install-mongodb)
- [Apps](#apps)
  - [Essential Apps](#essential-apps)
  - [Development Tools](#development-tools)
  - [Useful Apps](#useful-apps)
  - [Gaming Apps](#gaming-apps)
  - [Other](#other)
- [Git global configuration](#git-global-configuration)
  - [gitignore](#gitignore)
  - [gitconfig](#gitconfig)
- [Set up Git SSH Keys](#set-up-git-ssh-keys)
  - [Official documentation](#official-documentation)
  - [Initial configuration](#initial-configuration)
  - [Generate and add SSH keys](#generate-and-add-ssh-keys)
- [Set up GPG Keys to sign commits](#set-up-gpg-keys-to-sign-commits)
  - [Official documentation](#official-documentation)
  - [Install the GPG Suite](#install-the-gpg-Suite)
  - [Generating a GPG key](#generating-a-gpg-key)
  - [Add GPG keys to GitHub/GitLab account](#add-gpg-keys-to-github-gitlab-account)
  - [Associating GPG keys with Git](#associating-gpg-keys-with-git)
  - [Configuration for Tower.app](#configuration-for-tower.app)

## Install the Xcode Command Line Tools

```sh
$ xcode-select -p # Check if the full Xcode package is already installed
$ xcode-select --install # Install Xcode Command Line Tools
```

## Install Homebrew

Website: https://brew.sh

```sh
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
## Install and set up Zsh

More information on this [wiki page from Oh-My-Zsh](https://github.com/robbyrussell/oh-my-zsh/wiki/Installing-ZSH) and this [gist](https://gist.github.com/kevin-smets/8568070).

### Check if zsh is already installed

```sh
$ zsh --version # If installed, should be zsh 5.0 or more recent
$ echo $SHELL # Expected result should be /usr/bin/zsh or /bin/zsh
```

### Install zsh and make it the default shell

```sh
$ brew install zsh zsh-completions zsh-autosuggestions # Install zsh
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

### Add syntax highlighting

```sh
$ brew install zsh-syntax-highlighting
```

And add this __**to the end**__ of the `~/.zshrc` file:

```
# Add to end of the ~/.zshrc file
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

### Set window & tab title to current directory

In the `.zshrc` file:

```sh
DISABLE_AUTO_TITLE="true"

function precmd () {
  # window_title="\033]0;${PWD##*/}\007"
  if [[ -n $SSH_CONNECTION ]]; then
    window_title="\033]0;${USER}@${HOSTNAME%%.*}: ${PWD/#$HOME/~}\007"
  else
    window_title="\033]0;${PWD/#$HOME/~}\007"
  fi
  echo -ne "$window_title"
}
```

More information here:

- [setting terminal tab title](https://github.com/robbyrussell/oh-my-zsh/issues/5700)
- [Set the title of the terminal window to the current directory](https://superuser.com/questions/79972/set-the-title-of-the-terminal-window-to-the-current-directory)
- [Use PROMPT_COMMAND to set titles on iTerm tabs ](http://hints.macworld.com/article.php?story=20031015173932306)

## Install GNU ls for better ls colors

_GNU dircolors_ allows to use different colors theme when typing `ls` in the terminal. More information [here](https://github.com/seebi/dircolors-solarized) (make sure to read the quick note for macOS).

```sh
$ brew install coreutils
```

And add this alias in the `~/.zshrc` file:

```
alias ls="gls --color=auto"
```

## Install Emacs

```sh
$ brew install emacs
```

## Install Go

```sh
$ brew install go
```

## Install Node.js and npm

```sh
$ brew install node
```

## Install MySQL

```sh
$ brew install mysql # Install MySQL
$ brew services list # List the Homebrew services
$ brew services start mysql # Start the MySQL service
$ mysql -uroot -p # Start a MySQL shell
$ mysqladmin -u root password 'yourpassword' # Change root password
```

## Install PostgreSQL

Official guide: https://wiki.postgresql.org/wiki/Homebrew

```sh
$ brew install postgresql # Install PostgreSQL
$ brew services list # List the Homebrew services
$ brew services start postgresql # Start the PostgreSQL service
$ psql postgres # Start a PostgreSQL shell
```

## Install MongoDB

Official guide: https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/

```sh
$ brew tap mongodb/brew
$ brew install mongodb-community@5.0 # Install MongoDB
$ brew services list # List the Homebrew services
$ brew services start mongodb-community@5.0 # Start the MongoDB service
$ mongosh # Start a MongoDB shell
```

## Apps

### Essential Apps

| Name | Description | Paid? | Settings |
| ---------------- | ------------- |:-----:|:--------:|
| [1Password](https://1password.com/) | Password manager. | 💰 | |
| [Google Chrome](https://www.google.com/chrome/) | Web browser.  | | |
| [Microsoft Office](https://www.office.com) | Office productivity suite. | | |
| [Slack](https://www.slack.com) | Team communication app. | | |
| [Firefox Developer Edition](https://www.mozilla.org/en-US/firefox/developer/) | Web browser. | | |
| [Spark](https://itunes.apple.com/us/app/spark-love-your-email-again/id1176895641?mt=12) | Email desktop client. | | |
| [Fantastical 2](https://flexibits.com/fantastical) | Calendar desktop client. | 💰 | |
| [Magnet](https://itunes.apple.com/us/app/magnet/id441258766?mt=12) | Window manager. | 💰 | |
| [Google Play Music Desktop Player](https://www.googleplaymusicdesktopplayer.com/) | Google Play Music desktop client. | | |
| [OneDrive](https://itunes.apple.com/us/app/onedrive/id823766827?mt=12) | OneDrive syncing. | | |
| [Google Backup and Sync](https://www.google.com/drive/download/backup-and-sync/) | Google Drive syncing. | | |

### Development Tools

| Name | Description | Paid? | Settings |
| ---------------- | ------------- |:-----:|:--------:|
| [Tower](https://www.git-tower.com/) | Git desktop client. | 💰 | |
| [Kaleidoscope](https://www.kaleidoscopeapp.com/) | File comparison app (diff tool). | 💰 | |
| [Paw](https://paw.cloud/) | Full-featured HTTP client for API development (similar to Postman). | 💰 | |
| [iTerm2](https://www.iterm2.com/) | Terminal emulator for macOS. | | [Yes](./settings/iterm2) |
| [Hyper](http://hyper.is/) | JS/HTML/CSS Terminal. | | [Yes](./settings/hyper) |
| [Visual Studio Code](https://code.visualstudio.com/) | Source code editor. | | [Yes](./settings/vscode) |
| [Sublime Text](https://www.sublimetext.com/) | Source code editor. | | |
| [Xcode](https://itunes.apple.com/fr/app/xcode/id497799835?l=en&mt=12) | Official IDE for macOS, iOS, watchOS, and tvOS development. | | |
| [Android Studio](https://developer.android.com/studio/index.html) | Official IDE for Android development. | | |
| [Docker](https://www.docker.com/) | Create, deploy, and run applications by using containers. | | |
| [Sequel Pro](https://www.sequelpro.com/) | MySQL database management tool. | 💰 | |
| [Robo 3T](https://robomongo.org/) | MongoDB database management tool. | | |
| [DB Browser for SQLite](http://sqlitebrowser.org/) | SQLite database management tool. | | |

### Useful Apps

| Name | Description | Paid? | Settings |
| ---------------- | ------------- |:-----:|:--------:|
| [Pixelmator Pro](https://www.pixelmator.com/pro/) | Professional image editing tool. | 💰 | |
| [Cisco Webex Teams](https://www.webex.com/team-collaboration.html) | Team messaging app. | | |
| [VLC](https://www.videolan.org/vlc/index.html) | Multimedia player. | | |
| [Tweetbot](https://itunes.apple.com/us/app/tweetbot-for-twitter/id557168941?mt=12) | Twitter desktop client. | 💰 | |
| [Discord](https://discordapp.com/) | Voice & text chat app for gaming communities. | | |
| [Reflector](http://www.airsquirrels.com/reflector/) | Android & iOS wireless screen mirroring. | 💰 | |
| [Tuxera](https://www.tuxera.com/products/tuxera-ntfs-for-mac/) | NTFS drives read and write support. | 💰 | |
| [Gifox](https://gifox.io/) | GIF recording and sharing. | 💰 | |
| [Windscribe](https://windscribe.com/) | Free VPN and Ad Block. | | |
| [Sip](https://sipapp.io/)  | Color picker for macOS. | 💰 | |
| [LiveHome 3D](https://www.livehome3d.com/) | Home and Interior Design Software | 💰 | |
| [Ledger Live](https://www.ledger.com/pages/ledger-live) | Companion app for Ledger hardware wallet devices. | | |
| [Notion](https://www.notion.so/) | The all-in-one workspace for your notes, tasks, wikis, and databases. | | |
| [Paste](https://pasteapp.me/) | Cloud clipboard history & snippets manager. | 💰 | |
| [Meta](https://www.nightbirdsevolve.com/meta/) | Advanced Music Tag Editor for macOS. | 💰 | |

### Gaming Apps

| Name | Description | Paid? | Settings |
| ---------------- | ------------- |:-----:|:--------:|
| [Steam](http://store.steampowered.com/) | Gaming digital distribution platform. | | |
| [PS4 Remote Play](https://remoteplay.dl.playstation.net/remoteplay/lang/en/index.html) | Remote play for PlayStation 4. | | |

### Other

| Name | Description | Paid? | Settings |
| ---------------- | ------------- |:-----:|:--------:|
| [Adobe Photoshop](https://www.adobe.com/products/photoshop.html) | Photo, image and design editing tool. | 💰 | |
| [Sketch](https://www.sketchapp.com/) | Digital design toolkit. | 💰 | |
| [Parallels](https://www.parallels.com/) | Mac & Windows virtualization. | 💰 | |
| [Cornerstone](https://cornerstone.assembla.com/) | SVN client for macOS. | 💰 | |
| [The Archive Browser](https://theunarchiver.com/archive-browser) | Browser for archive type files (zip, rar, 7-zip, tar, etc). | 💰 | |
| [Texpad](https://www.texpad.com/osx) | LaTeX editor. | 💰 | |

## Git global configuration

### gitignore

```sh
$ curl https://raw.githubusercontent.com/github/gitignore/master/Global/macOS.gitignore -o ~/.gitignore_global
```

### gitconfig

```sh
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
$ git config --global core.editor emacs
$ git config --global core.excludesfile ~/.gitignore_global
```

## Set up Git SSH Keys

### Official documentation

- [GitHub](https://help.github.com/articles/connecting-to-github-with-ssh/)
- [GitLab](https://docs.gitlab.com/ee/ssh/README.html)

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

- `Settings > SSH and GPG keys > New SSH key` for [**GitHub**](https://github.com/settings/ssh/new).
- `Settings > SSH Keys` for [**GitLab**](https://gitlab.com/profile/keys).

## Set up GPG Keys to sign commits

### Official documentation

- [GitHub](https://help.github.com/articles/signing-commits-using-gpg/)
- [GitLab](https://docs.gitlab.com/ee/user/project/repository/gpg_signed_commits/)

### Install the GPG Suite

Download and install the GPG Suite from the [official website](https://gpgtools.org/).

### Generating a GPG key

```sh
$ gpg --full-gen-key
```

And follow the instructions. Recommended value for RSA keys is 4096 bits long (highest value). Pick a strong password when asked and type it twice to confirm.

### Add GPG keys to GitHub/GitLab account

```sh
$ gpg --list-secret-keys --keyid-format LONG <email_address>
# Copy the GPG key ID that starts with 'sec' and after 'rsa4096/'
$ gpg --armor --export <gpg_key_id> | pbcopy
```

Then paste the content of the clipboard in:

- `Settings > SSH and GPG keys > New GPG key` for [**GitHub**](https://github.com/settings/gpg/new).
- `Settings > GPG Keys` for [**GitLab**](https://gitlab.com/profile/gpg_keys).

### Associating GPG keys with Git

```sh
$ gpg --list-secret-keys --keyid-format LONG <email_address>
# Copy the GPG key ID that starts with 'sec' and after 'rsa4096/'
$ cd <your_git_project> # To associate GPG keys on a project-to-project basis rather than globally
$ git config user.signingkey <gpg_key_id>
$ git config commit.gpgsign true
```

### Configuration for Tower.app

Some helpful links:
- [Signing GitHub Commits](https://www.fabianehlert.com/post/signingcommits/)
- [GPG and git on macOS](https://gist.github.com/danieleggert/b029d44d4a54b328c0bac65d46ba4c65)
- [Sign your commits with Tower.app](https://stefanzweifel.io/posts/sign-your-commits-with-tower-app)

```sh
$ git config --global gpg.program /usr/local/MacGPG2/bin/gpg2
$ echo no-tty >> ~/.gnupg/gpg.conf
```
