# SQLCipher Change Log
All notable changes to this project will be documented in this file.

## [unreleased] - [unreleased]

## [4.0.1] - 2018-12-17
- Based on upstream SQLite 3.26.0 (addresses SQLite “Magellan” issue)
- Adds PRAGMA cipher_compatibility and cipher_default_compatibility which take automatcially configure appropriate compatibility settings for the specified SQLCipher major version number
- Filters attach statements with KEY parameters from readline history
- Fixes crash in command line shell with empty input (i.e. ^D)
- Fixes warnings when compiled with strict-prototypes

## [4.0.0] - 2018-11-30
### Changed
- Default page size for databases increased to 4096 bytes (up from 1024) *
- Default PBKDF2 iterations increased to 256,000 (up from 64,000) *
- Default KDF algorithm is now PBKDF2-HMAC-SHA512 (from PBKDF2-HMAC-SHA1) *
- Default HMAC algorithm is now HMAC-SHA512 (from HMAC-SHA1) *
- PRAGMA cipher is now disabled and no longer supported (after multi-year deprecation) *
- PRAGMA rekey_cipher is now disabled and no longer supported *
- PRAGMA rekey_kdf_iter is now disabled and no longer supported *
- By default all memory allocated internally by SQLite before the memory is wiped before it is freed 
- PRAGMA cipher_memory_security: allows full memory wiping to be disabled for performance when the feature is not required
- PRAGMA cipher_kdf_algorithm, cipher_default_kdf_algorithm to control KDF algorithm selection between PBKDF2-HMAC-SHA1, PBKDF2-HMAC-SHA256 and PBKDF2-HMAC-SHA512
- PRAGMA cipher_hmac_algorithm, cipher_default_hmac_algorithm to control HMAC algorithm selection between HMAC-SHA1, HMAC-SHA256 and PBKDF2-HMAC-SHA512
- Based on upstream SQLite 3.25.2
- When compiled with readline support, PRAGMA key and rekey lines will no longer be
  saved to history
- Adds second optional parameter to sqlcipher_export to specify source database to
  support bidirectional exports
- Fixes compatibility with LibreSSL 2.7.0+
- Fixes compatibility with OpenSSL 1.1.x
- Simplified and improved performance for PRAGMA cipher_migrate when migrating older database versions
- Refactoring of SQLCipher tests into separate files by test type
- PRAGMA cipher_plaintext_header_size and cipher_default_plaintext_header_size: allocates a portion of the database header which will not be encrypted to allow identification as a SQLite database
- PRAGMA cipher_salt: retrieve or set the salt value for the database
- Adds Podspec for using tagged versions of SQLCipher
- Define SQLCIPHER_PROFILE_USE_FOPEN for WinXP support
- Improved error handling for cryptographic providers
- Improved memory handling for PRAGMA commands that return values
- Improved version reporting to assist with identification of distribution
- Major rewrite and simplification of internal codec and pager extension
- Fixes compilation with --disable-amalgamation
- Removes sqlcipher.xcodeproj build support

## [3.4.2] - 2017-12-21
### Added
- Added support for building with LibreSSL

### Changed
- Merge upstream SQLite 3.20.1
- Text strings for `SQLITE_ERROR` and `SQLITE_NOTADB` changed to match upstream SQLite
- Remove static modifier for codec password functions
- Page alignment for `mlock`
- Fix segfault in `sqlcipher_cipher_ctx_cmp` during rekey operation
- Fix `sqlcipher_export` and `cipher_migrate` when tracing API in use
- Validate codec page size when setting
- Guard OpenSSL initialization and cleanup routines
- Allow additional linker options to be passed via command line for Windows platforms

## [3.4.1] - 2016-12-28
### Added
- Added support for OpenSSL 1.1.0

### Changed
- Merged upstream SQLite 3.15.2

## [3.4.0] - 2016-04-05
### Added
- Added `PRAGMA cipher_provider_version`

### Changed
- Merged upstream SQLite 3.11.0

### Deprecated
- Deprecated `PRAGMA cipher` command

## [3.3.1] - 2015-07-13
### Changed
- Merge upstream SQLite 3.8.10.2
- Fixed segfault when provided an invalid cipher name
- Check for codec context when performing `PRAGMA cipher_store_pass`
- Remove extraneous null check in `PRAGMA cipher_migrate`

## [3.3.0] - 2015-03-25
### Added
- Added FIPS API calls within the OpenSSL crypto provider
- `PRAGMA cipher_default_page_size` - support for attaching non-default page sizes

### Changed
- Merged upstream SQLite 3.8.8.3

## [3.2.0] - 2014-09-30
### Added
- Added `PRAGMA cipher_store_pass`

### Changed
- Merged upstream SQLite 3.8.6
- Renmed README to README.md

## [3.1.0] - 2014-04-23
### Added
- Added `PRAGMA cipher_profile`

### Changed
- Merged upstream SQLite 3.8.4.3

## [3.0.1] - 2013-12-06
### Added
- Added `PRAGMA cipher_add_random` to source external entropy

### Changed
- Fix `PRAGMA cipher_migrate` to handle passphrases longer than 64 characters & raw keys
- Improvements to the libtomcrypt provider

## [3.0.0] - 2013-11-05
### Added
- Added `PRAGMA cipher_migrate` to migrate older database file formats

### Changed
- Merged upstream SQLite 3.8.0.2
- Remove usage of VirtualLock/Unlock on WinRT and Windows Phone
- Ignore HMAC read during Btree file copy
- Fix lib naming for pkg-config
- Use _v2 version of `sqlite3_key` and `sqlite3_rekey`
- Update xcodeproj file

### Security
- Change KDF iteration length from 4,000 to 64,000

[unreleased]: https://github.com/sqlcipher/sqlcipher/compare/v4.0.1...prerelease
[4.0.1]: https://github.com/sqlcipher/sqlcipher/compare/v4.0.0...v4.0.1
[4.0.0]: https://github.com/sqlcipher/sqlcipher/compare/v3.4.2...v4.0.0
[3.4.2]: https://github.com/sqlcipher/sqlcipher/compare/v3.4.1...v3.4.2
[3.4.1]: https://github.com/sqlcipher/sqlcipher/compare/v3.4.0...v3.4.1
[3.4.0]: https://github.com/sqlcipher/sqlcipher/compare/v3.3.1...v3.4.0
[3.3.1]: https://github.com/sqlcipher/sqlcipher/compare/v3.3.0...v3.3.1
[3.3.0]: https://github.com/sqlcipher/sqlcipher/compare/v3.2.0...v3.3.0
[3.2.0]: https://github.com/sqlcipher/sqlcipher/compare/v3.1.0...v3.2.0
[3.1.0]: https://github.com/sqlcipher/sqlcipher/compare/v3.0.1...v3.1.0
[3.0.1]: https://github.com/sqlcipher/sqlcipher/compare/v3.0.0...v3.0.1
[3.0.0]: https://github.com/sqlcipher/sqlcipher/compare/v2.2.0...v3.0.0
[2.2.0]: https://github.com/sqlcipher/sqlcipher/compare/v2.1.1...v2.2.0
[2.1.1]: https://github.com/sqlcipher/sqlcipher/compare/v2.1.0...v2.1.1
[2.1.0]: https://github.com/sqlcipher/sqlcipher/compare/v2.0.6...v2.1.0
[2.0.6]: https://github.com/sqlcipher/sqlcipher/compare/v2.0.5...v2.0.6
[2.0.5]: https://github.com/sqlcipher/sqlcipher/compare/v2.0.3...v2.0.5
[2.0.3]: https://github.com/sqlcipher/sqlcipher/compare/v2.0.0...v2.0.3
[2.0.0]: https://github.com/sqlcipher/sqlcipher/compare/v1.1.10...v2.0.0
[1.1.10]: https://github.com/sqlcipher/sqlcipher/compare/v1.1.9...v1.1.10
[1.1.9]: https://github.com/sqlcipher/sqlcipher/compare/v1.1.8...v1.1.9
[1.1.8]: https://github.com/sqlcipher/sqlcipher/compare/v1.1.7...v1.1.8
[1.1.7]: https://github.com/sqlcipher/sqlcipher/compare/v1.1.6...v1.1.7
[1.1.6]: https://github.com/sqlcipher/sqlcipher/compare/v1.1.5...v1.1.6
[1.1.5]: https://github.com/sqlcipher/sqlcipher/compare/v1.1.4...v1.1.5
[1.1.4]: https://github.com/sqlcipher/sqlcipher/compare/v1.1.3...v1.1.4
[1.1.3]: https://github.com/sqlcipher/sqlcipher/compare/v1.1.2...v1.1.3
[1.1.2]: https://github.com/sqlcipher/sqlcipher/compare/v1.1.1...v1.1.1
[1.1.1]: https://github.com/sqlcipher/sqlcipher/compare/v1.1.0...v1.1.1
[1.1.0]: https://github.com/sqlcipher/sqlcipher/compare/617ed01...v1.1.0
