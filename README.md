TODO FORMATTING!

Connect to network
    $ sudo raspi-config

Install Rust:
    $ curl --proto 'https' --tlsv1.2 -sSf https://sh.rustup.rs | rs

Install Solana SLI from source (for aarch64-unknown-linux-gnu)
    Update and install dependencies
    $ sudo apt update
    $ sudo apt install -y clang libclang-dev pkg-config build-essential libudev-dev libssl-dev
    Increase swap size to 4GB
    $ sudo dphys-swapfile swapoff
    $ sudo sudo nvim /etc/dphys-swapfile
        Set filesize to 4096Mb
    $ sudo dphys-swapfile setup
    $ sudo dphys-swapfile swapon
    Clone repo
    $ git clone --depth 1 https://github.com/anza.xyz/agave.git solana-agave
    $ cd solana-agave
    Build from source
    (For PI 4 4GB) In ./scripts/cargo-install-all.sh add "-j 1" to the cargo_build() function call or else the PI (4GB) will run out of memory.
    $ ./scripts/cargo-install-all.sh ~/.cargo/bin
        Build time ~5h
    Remove conflicting yarn installation if needed
    $ sudo apt remove --purge cmdtest
    $ sudo apt remove --purge yarn
    $ sudo apt autoremove -y # Clean up unused dependencies
    Install nodejs and npm 
    $ sudo apt install -y nodejs npm 
    Install nvm and set correct node version (PI LTS is 18, we need 20)
    $ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
    $ export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
        [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
    $ nvm install 20
    $ nvm use 20
    Install yarn
    $ sudo npm install --global yarn

Notes:
    NVIM
        :set wrap # Wraps the text. Helpful on small screens.
i   Rust
        Use "cargo add <pkg> --offline" to pull a pkg from the download cache instead of online
