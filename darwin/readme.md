# macOS suckless settings

## Setup `Homebrew` and Apps

- Install requirments: `Xcode` and `Homebrew`[^1]:

  ```sh
  xcode-select --install
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  ```

- Install Apps[^2]:

  - Brew apps:

  ```sh
  brew tap alienator88/cask
  brew tap th-ch/youtube-music
  xargs brew install --cask < brew_apps.txt
  xattr -cr /Applications/YouTube\ Music.app # if get an error "is damaged and can’t be opened."
  ```

  - [Gems](https://www.gems.so/) : check email for download links
  - [Secure ShellFish](https://secureshellfish.app/): install from App Store.
  - [Logi Option+](https://www.logitech.com/software/logi-options-plus.html#customization-app-download): install it from brew breaks it too often.

- Import `Raycast` configs:
  - Open raycast: `Import Settings and Data`.

## Setup IME

- [vChewing-macOS](https://github.com/vChewing/vChewing-macOS)

## Setup nix/home-manager

- check [here](https://github.com/CharlesChiuGit/nix-hm-config)

[^1]: https://github.com/Homebrew/install/

[^2]: https://brew.sh/
