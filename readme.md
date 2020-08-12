# packetcrypt_rs
PacketCrypt implementation in Rust

## What exists
PacketCrypt mining is made up of 6 distinct components:
* Master - provides work and config files to everyone for a given pool
* Announcement Miner - generates announcements (data which uses bandwidth)
* Announcement Handler - consumes announcements, checks validity and provides to block miner
* Block Miner - uses announcements for for mining blocks
* Block Handler - takes shares from Block Miner and validates them
* Paymaker - takes messages from Block Handler and Announcement Handler to
decide which miners the pool should pay

The Master, Announcement Handler, Block Handler, and Paymaker must be operated
by the mining pool, the Announcement Miner and Block Miner can be operated by 3rd
parties.

This codebase currently provides the *Announcement Handler* and *Announcement Miner* components.
All of the others can be found in
[the C PacketCrypt project](https://github.com/cjdelisle/PacketCrypt).

## Install
* Install rust if you haven't, see: [rustup](https://rustup.rs/)
* Install using cargo: `cargo install packetcrypt`

## Mine announcements

* `packetcrypt ann <pool url> --paymentaddr <your PKT addr>`

For more information `packetcrypt help ann`

## Run an Announcement Handler
If you're running a pool, you can use the Rust announcement handler as follows:
* `packetcrypt ah -C /path/to/pool.toml`

See [pool.example.toml](https://github.com/cjdelisle/packetcrypt_rs/blob/master/pool.example.toml)
for information about what should be in your pool.toml file.

For more information `packetcrypt help ah`

## Env vars
* `RUST_LOG=packetcrypt=debug` for better logging
* `RUST_BACKTRACE=1` for backtraces on errors (including non-critical ones)

## License

LGPL-2.1 or LGPL-3.0, at your option