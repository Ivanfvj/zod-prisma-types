# Changelog

All notable changes to this project will be documented in this file.

## [4.0.0] - 2025-09-15

### Added
- Zod v4 compatibility support
- Support for new `z.record()` API that requires explicit key types

### Changed
- **BREAKING**: Updated zod dependency from v3.x to v4.x
- Updated `z.record()` calls in JSON value schemas to be compatible with Zod v4:
  - In `writeJsonValue.ts`: Added explicit key type `z.union([z.string(), z.number(), z.symbol()])`
  - In `writeInputJsonValue.ts`: Added explicit key type `z.string()` and changed to use `.nullable()`
- Package name changed to `@ivanfvj/zod-prisma-types` (scoped package)

### Migration Guide
To upgrade from the original `zod-prisma-types` package:

1. Uninstall the old package: `npm uninstall zod-prisma-types`
2. Install this fork: `npm install @ivanfvj/zod-prisma-types`
3. Update your Prisma schema generator config:
   ```prisma
   generator zod {
     provider = "@ivanfvj/zod-prisma-types"
     output   = "./zod"
   }
   ```
4. Ensure you're using Zod v4: `npm install zod@^4.0.0`

### Credits
- Original package by Chris Hörmann (https://github.com/chrishoermann/zod-prisma-types)
- Zod v4 compatibility patch inspired by community contributions in issue #332