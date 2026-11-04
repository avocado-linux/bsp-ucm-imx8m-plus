# Changelog

All notable changes to avocado-bsp-ucm-imx8m-plus are documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.1]

### Added
- Build and publish on the 2026 feed (edge and next), alongside 2024.

### Removed
- `kernel-module-crct10dif-ce`: 6.18 folds the arm64 CRC-T10DIF code into
  `crc-t10dif`, so the package doesn't exist on 2026. The kernel loads the CRC
  module it needs on demand, so the BSP doesn't need to name it.
- `kernel-module-evbug`: a debug driver that logs every input event to the
  kernel log. It isn't built on 2026 and shouldn't load on a product.

## [0.1.0]

### Added
- Initial release: Board support for the CompuLab UCM-iMX8M-Plus SOM.
- CI via the shared `avocado-linux/actions` reusable workflows: PR build check
  (`test.yml`) and tag-driven package + publish to the Avocado feed (`release.yml`).
