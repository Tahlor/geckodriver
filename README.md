# Building help
    https://firefox-source-docs.mozilla.org/testing/geckodriver/Building.html
# Github
    https://github.com/mozilla/geckodriver    
# Source
    https://hg.mozilla.org/mozilla-central/file/tip/testing/geckodriver

# Download source

    #curl https://hg.mozilla.org/mozilla-central/archive/tip.zip/testing/geckodriver/ > t.zip
    curl https://hg.mozilla.org/mozilla-central/archive/tip.zip/testing/ > t.zip
    unzip t.zip

# Build
# Install RUST
    curl https://sh.rustup.rs -sSf | sh

# Install cross-compiler toolchain:
    apt install gcc-arm-linux-gnueabihf libc6-armhf-cross libc6-dev-armhf-cross

# Create a new shell, or to reuse the existing shell:
    source $HOME/.cargo/env

#Install rustc target toolchain:

    rustup target install armv7-unknown-linux-gnueabihf

# Put this in testing/geckodriver/.cargo/config:

    [target.armv7-unknown-linux-gnueabihf]
    linker = "arm-linux-gnueabihf-gcc"

# Build geckodriver from testing/geckodriver:

    cd testing/geckodriver
    cargo build --release --target armv7-unknown-linux-gnueabihf

# Grab it!
    cp "./mozilla-central-cd7d8aad0306/testing/geckodriver/target/armv7-unknown-linux-gnueabihf/release/geckodriver" ./
