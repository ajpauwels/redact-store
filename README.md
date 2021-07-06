
# redact-store
[![License: GPL-3.0](https://img.shields.io/badge/License-GPL3.0-yellow.svg)](https://opensource.org/licenses/GPL-3.0) [![Coverage Status](https://coveralls.io/repos/github/pauwels-labs/redact-store/badge.svg?branch=main)](https://coveralls.io/github/pauwels-labs/redact-store?branch=main) [![docs.rs](https://docs.rs/redact-store/badge.svg)](https://docs.rs/redact-store/badge.svg) ![crates.io](https://img.shields.io/crates/v/redact-store?style=flat-square)

redact-store is a storage server 

## Setup
redact-store currently only supports being run with a MongoDB back-end, although more will be added in the future. There are a couple options for getting a free mongo database:
1. Get a 100% free, fully-managed database at [mongodb.com](https://mongodb.com) (easier, available from any device)
2. Host it locally by installing and running mongo (harder, only available locally)

The storage server simply takes in a connection string and database name and is agnostic to where the database is hosted.

## Run
1. `git clone https://github.com/pauwels-labs/redact-crypto`
2. `echo "export REDACT_DB_URL=\"<mongo connection string>\"" >> config/config.env`
3. `echo "export REDACT_DB_NAME=\"<db name>\"" >> config/config.env`
4. `source config/config.env`
5. `cargo r`

## Usage
- Get data route. This route takes in a data path and will return the data at that path if it exists.
	- `GET /<path>`
	- `<path>` is a jsonpath-style string prepended and appended by a period, e.g. `.profile.firstName.`
- Post data route. This route access an entire data entry and will store it in the database if possible.
	- `POST /`
	- The body of the request should be an `Entry` struct serialized as JSON

## Test
To run unit tests:
1. `cargo t`

To run unit tests+code coverage output (does not work on macos or windows):
1. `cargo install tarpaulin`
2. `cargo tarpaulin -o html`
