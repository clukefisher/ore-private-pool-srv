# Yolo and Solo Your Private Pool for ORE Mining

**The goal of this project is to balance the ever-growing public pools and decentralize computing power, in line with the ORE design principle: anyone can mine. As expected, more individual miners.**

**This is private pool server. Forked from [ore-hq-server](https://github.com/Kriptikz/ore-hq-server.git).**

It's tailored by Miraland Labs as a lightweight release, **derived from and credited to ore-hq-server.**

## Key Differentiators of the Private Pool

**Simplified and lightweight.**

**Optimized for home and/or personal use.**

**Zero fee charge for computing client, mining tx fee only for pool server.**

**No delegate.**

**Embedded lightweight database as an option.**

**Scale from a few to tens of devices, either laptop or PC.**

**Balance between worse penalties and better rewards.**

**Easy setup and flexible home deployment.**

## ORE Private Pool Community

Private pool operators can discuss and help each other at:

-   [ORE Private Pool Discord](https://discord.gg/YjQhWqxp7H)

## Install

ORE Private Pool installation consists of 2 parts: server and clients. One server will serve multiple clients. The following is for server installation (ore-private-pool-srv). To install clients, please refer to [client installation(ore-private-pool-cli)](https://crates.io/crates/ore-private-pool-cli).

To install the private pool server, 2 approaches are recommended:

**Approach One**: install from crates.io directly, use [cargo](https://doc.rust-lang.org/cargo/getting-started/installation.html):

```sh
cargo install ore-private-pool-srv
```

**Approach Two**: download source code from Github at: [github](https://github.com/miraland-labs/ore-private-pool-srv):

```sh
https://github.com/miraland-labs/ore-private-pool-srv
```

and then compile locally

`cargo build --release`

### Dependencies

If you run into issues during installation, please install the following dependencies for your operating system and try again:

#### Linux

```
sudo apt-get update
sudo apt-get install openssl pkg-config libssl-dev gcc
```

Notes: you may need to install dependencies to enable sound notification on ubuntu OS with:

```
sudo apt-get install libasound2-dev
sudo apt-get install libudev-dev
```

#### MacOS (using [Homebrew](https://brew.sh/))

```
brew install openssl pkg-config

# If you encounter issues with OpenSSL, you might need to set the following environment variables:
export PATH="/usr/local/opt/openssl/bin:$PATH"
export LDFLAGS="-L/usr/local/opt/openssl/lib"
export CPPFLAGS="-I/usr/local/opt/openssl/include"
```

#### Windows (using [Chocolatey](https://chocolatey.org/))

```
choco install openssl pkgconfiglite
```

#### rust (if not installed yet)

Open a terminal window on Mac / Linux / BSD / Windows PowerShell:

```
curl https://sh.rustup.rs -sSf | sh
```

or

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

## Build

To build the codebase from scratch, checkout the repo and use cargo to build:

```sh
cargo build --release
```

## Env Settings

copy `.env.example` file and rename to `.env`, set with your own settings.

## Run

To run pool server, execute:

```sh
ore-ppl-srv [OPTIONS]
```

or, if you build from source code downloaded from github, enter into ore-private-pool-srv home directory,
duplicate `bin.example` directory and rename to `bin`, modify settings in `start-ore-ppl-srv.sh`, execute:

```
bin/start-ore-ppl-srv.sh
```

or, with log filter specified as follows:

```
RUST_LOG=info bin/start-ore-ppl-srv.sh
```

if you only want to output a log with the level warn or error, you can replace `info` with `warn` or `error`. By default(without specifying RUST_LOG), your standard output(terminal) will display a log with level `info`, and the log files will be written with level `trace`.

There are 2 types of daily log files in the `logs' subdirectory. One type is server_log with the filename pattern ore-ppl-srv.log.yyyy-mm-dd, the other type is contribution_log with the filename pattern ore-ppl-contributions.log.yyyy-mm-dd. By default, the server log with filtered content is redirected to standard output or the terminal.

## Help

You can use the `-h` flag on any command to pull up a help menu with documentation:

```sh
ore-ppl-srv -h

Usage: ore-ppl-srv [OPTIONS]

Options:
-b, --buffer-time <BUFFER_SECONDS>
        The number seconds before the deadline to stop mining and start submitting. [default: 5]
-r, --risk-time <RISK_SECONDS>
        Set extra hash time in seconds for miners to stop mining and start submitting, risking a penalty. [default: 0]
--priority-fee <FEE_MICROLAMPORTS>
        Price to pay for compute units when dynamic fee flag is off, or dynamic fee is unavailable. [default: 100]
--priority-fee-cap <FEE_CAP_MICROLAMPORTS>
        Max price to pay for compute units when dynamic fees are enabled. [default: 100000]
--dynamic-fee
        Enable dynamic priority fees
--dynamic-fee-url <DYNAMIC_FEE_URL>
        RPC URL to use for dynamic fee estimation.
-e, --expected-min-difficulty <EXPECTED_MIN_DIFFICULTY>
        The expected min difficulty to submit from pool client. Reserved for potential qualification process unimplemented yet. [default: 8]
-e, --extra-fee-difficulty <EXTRA_FEE_DIFFICULTY>
        The min difficulty that the pool server miner thinks deserves to pay more priority fee to land tx quickly. [default: 29]
-e, --extra-fee-percent <EXTRA_FEE_PERCENT>
        The extra percentage that the pool server miner feels deserves to pay more of the priority fee. As a percentage, a multiple of 50 is recommended(example: 50, means pay extra 50% of the specified priority fee), and the final priority fee cannot exceed the priority fee cap. [default: 0]
-s, --slack-difficulty <SLACK_DIFFICULTY>
        The min difficulty that will notify slack channel(if configured) upon transaction success. [default: 25]
  -m, --messaging-diff <MESSAGING_DIFF>
        The min difficulty that will notify messaging channels(if configured) upon transaction success. [default: 25]
      --send-tpu-mine-tx
        Send and confirm transactions using tpu client.
--no-sound-notification
        Sound notification on by default
```

## Support us | Donate at your discretion

We greatly appreciate any donation to help support projects development at Miraland Labs. Miraland is dedicated to freedom and individual sovereignty and we are doing our best to make it a reality.
Certainly, if you find this project helpful and would like to support its development, you can buy me/us a coffee!
Your support is greatly appreciated. It motivates me/us to keep improving this project.

**Bitcoin(BTC)**
`bc1plh7wnl0v0xfemmk395tvsu73jtt0s8l28lhhznafzrj5jwu4dy9qx2rpda`

![Donate BTC to Miraland Development](donations/donate-btc-qr-code.png)

**Solana(SOL)**
`9h9TXFtSsDAiL5kpCRZuKUxPE4Nv3W56fcSyUC3zmQip`

![Donate SOL to Miraland Development](donations/donate-sol-qr-code.png)

Thank you for your support!
