# NFT-
require('babel-register'); require('babel-polyfill');  module.exports = {   networks: {     development: {       host: "127.0.0.1",       port: 7545,       network_id: "*" // Match any network id     },   },   contracts_directory: './src/contracts/',   contracts_build_directory: './src/abis/',   compilers: {     solc: {       optimizer: {         enabled: true,         runs: 200       }     }   } }
#!/bin/bash
TARGET="${CARGO_TARGET_DIR:-target}"
set -e
cd "`dirname $0`"

cargo build --all --target wasm32-unknown-unknown --release
cp $TARGET/wasm32-unknown-unknown/release/defi.wasm ./res/
cp $TARGET/wasm32-unknown-unknown/release/fungible_token.wasm ./res/
