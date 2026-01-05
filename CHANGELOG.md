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

### Changed

- CPack is now used for mod packaging

### Removed

- CMake option ENABLE_MOD_ARCHIVE
- CMake option MOD_ARCHIVE_DIR
- CMake option MOD_ARCHIVE_FOLDER

### Community fixes

- Always return m_iSecondaryAmmoType from CBasePlayerWeapon::SecondaryAmmoIndex  ([34ce0e3](https://github.com/twhl-community/halflife-updated/commit/34ce0e346060a2b4b40c941af6c6d2bb18b3023b)) (Thanks Solokiller)
- Fix autoaim angles not resetting if autoaim is disabled while aiming at a target ([beb9f35](https://github.com/twhl-community/halflife-updated/commit/beb9f35e4ca4008369889fd8722c95220dc44a4d)) (Thanks Solokiller)
- Fix weapon being left behind when picking up ammo from it ([d42b905](https://github.com/twhl-community/halflife-updated/commit/d42b905be6aa0d12a2a4615fc84273958ed2f315)) (Thanks Solokiller)
- Fix Python repeatedly playing dry fire sound & glitching animation when holding primary attack with empty magazine ([75bc5af](https://github.com/twhl-community/halflife-updated/commit/75bc5af5ab62a387a07f69edd34b42ebb12e8fe1)) (Thanks Solokiller)
- Fix server not staying in sync with client when handling weapon attack times ([b466921](https://github.com/twhl-community/halflife-updated/commit/b4669215d0bff76b6051a8f79c50917d4c75d277) and [343ebf2](https://github.com/twhl-community/halflife-updated/commit/343ebf2495e96eb3a5adda4d0ab0f28065be4c83)) (Thanks Solokiller)
- Fix chainsaw crowbar effect when hitting corpse ([511c6ef](https://github.com/twhl-community/halflife-updated/commit/511c6ef6271692ec391bee61e53addc6dbe79fa6)) (Thanks Solokiller)
- Add null check to bullsquid spit attack animation event to prevent crash if enemy pointer is cleared between animation start and animation event occurrence ([4544719](https://github.com/twhl-community/halflife-updated/commit/454471956c7a4fe5c22a09c382afa4cb439c7702)) (Thanks Solokiller)
- Add check to make sure fread calls succeeded before using results ([d737eb4](https://github.com/twhl-community/halflife-updated/commit/d737eb4649d10e01dbfcfba455068ba6323506ae)) (Thanks Solokiller)
- Add error check to getcwd call to prevent potential garbage paths from being used to load libraries ([66ce8bb](https://github.com/twhl-community/halflife-updated/commit/66ce8bb0fbfb6de185c4f4250ea3f6141fd1babc)) (Thanks Solokiller)
- Increase buffer sizes to ensure all potential inputs can fit without overflowing the buffer ([faca810](https://github.com/twhl-community/halflife-updated/commit/faca8108f2a5180add4dc657624e0ebe71f7947a)) (Thanks Solokiller)
- Remove obsolete macros & conditional code compilation ([1c85751](https://github.com/twhl-community/halflife-updated/commit/1c857514f39a97da4140e844b83c45aa33622179)) (Thanks Solokiller)
- Make sure string buffers are large enough for format operations ([d7e6c42](https://github.com/twhl-community/halflife-updated/commit/d7e6c42b5dd6606ad97f79bd92278cd6d3721c66)) (Thanks Solokiller)
- Make sure string buffer is large enough for format operation ([c327550](https://github.com/twhl-community/halflife-updated/commit/c3275508993a757b5310b4376cfb582f0b3ac498)) (Thanks Solokiller)
- Correctly scope for loop variables to silence compiler warnings ([8cde048](https://github.com/twhl-community/halflife-updated/commit/8cde04881e8aa329a539e80f82330ea2f1c9932c)) (Thanks Solokiller)
- Fix invalid uses of NULL macro ([7be78fe](https://github.com/twhl-community/halflife-updated/commit/7be78fe21ab522fff79f04100fab274f4bfee77a)) (Thanks Solokiller)
- Remove EHANDLE::operator int ([3bf4413](https://github.com/twhl-community/halflife-updated/commit/3bf44134c4b65d06975fcf2aec89fbdedd993660)) (Thanks Solokiller)
- Use 0 instead of NULL to set HSPRITE handle to nothing ([47edc4d](https://github.com/twhl-community/halflife-updated/commit/47edc4dd332baaa937764652f505922518f185a7)) (Thanks Solokiller)
- Fix incorrect uses of sprintf ([133c256](https://github.com/twhl-community/halflife-updated/commit/133c256ebcd1ee352470919316d096754970a797)) (Thanks Solokiller)
- Fix incorrect for loop variable scope breaking team selection logic ([36380cd](https://github.com/twhl-community/halflife-updated/commit/36380cd0c96798432260ea66a54db23ea1e9ca61)) (Thanks Solokiller)
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

## [1.0.1] - 2025-12-21

### Fixed

- Fix m_rawinput 1 getting mouse stuck in box (Thanks Solokiller)

## [1.0.0] - 2021-11-07

### Added

- Initial release
