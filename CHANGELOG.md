# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- C++20 support
- Build metadata to CMake and `modinfo`
- Prerelease version support to CMake and `modinfo`
- Visual Studio 2026 support
- 25th anniversary changes

### Fixed

- Always return m_iSecondaryAmmoType from CBasePlayerWeapon::SecondaryAmmoIndex  ([34ce0e3](https://github.com/twhl-community/halflife-updated/commit/34ce0e346060a2b4b40c941af6c6d2bb18b3023b)) (Thanks Solokiller)
- Fix incorrect uses of sprintf ([8a64f04](https://github.com/twhl-community/halflife-updated/commit/8a64f04ce679f6d593fa9c6caa5a246daea394ae)) (Thanks Solokiller)
- Fix scientists not disregarding enemy after hiding ([fc8c85f](https://github.com/twhl-community/halflife-updated/commit/fc8c85f3dccb4f80669f6ff15d406b9fe92a2629)) (Thanks Revenant100)
- Removing redundant scientist scream ([f748eb8](https://github.com/twhl-community/halflife-updated/commit/f748eb8c8a19894da0d13abb577fbcb89a5c744e)) (Thanks Revenant100)
- Fix scientists not screaming in fear ([57306ca](https://github.com/twhl-community/halflife-updated/commit/57306ca1cbea73f238b465a18eb35c31d9099181)) (Thanks Revenant100)
- Restore scientist's fear display animation ([992e4cf](https://github.com/twhl-community/halflife-updated/commit/992e4cf79871f4c43dbdc5bee099ac0e0abb51c9)) (Thanks Revenant100)
- Restore scientist's sense of smell ([1d88ba8](https://github.com/twhl-community/halflife-updated/commit/1d88ba86faa46aa9554d962399bea18d0045bbe4)) (Thanks Revenant100)
- Restore being able to damage AFlocks ([ab037f6](https://github.com/twhl-community/halflife-updated/commit/ab037f6d7b9498bb8bbf4517f0adaf4df5c87487)) (Thanks Revenant100)
- Fix scientists not fearing Alien Grunts and Bullsquids ([75bf517](https://github.com/twhl-community/halflife-updated/commit/75bf517d1e9d828b89ae99035142134f0ffff932)) (Thanks Revenant100)
- Fix various instances of Houndeyes not correctly blinking/closing eyes ([e5f9c39](https://github.com/twhl-community/halflife-updated/commit/e5f9c393348fb42bcb3e8618f162f4bf43450db0)) (Thanks Revenant100)
- Restoring Houndeye's squad leader leaderlook animation ([c718785](https://github.com/twhl-community/halflife-updated/commit/c718785acd5baae691f504875597156e8d64622c)) (Thanks Revenant100)

### Changed

- CPack is now used for mod packaging

### Removed

- CMake option ENABLE_MOD_ARCHIVE
- CMake option MOD_ARCHIVE_DIR
- CMake option MOD_ARCHIVE_FOLDER

## [1.0.1] - 2025-12-21

### Fixed

- Fix m_rawinput 1 getting mouse stuck in box (Thanks Solokiller)

## [1.0.0] - 2021-11-07

### Added

- Initial release
