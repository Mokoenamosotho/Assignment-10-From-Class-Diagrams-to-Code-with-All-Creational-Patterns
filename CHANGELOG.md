# Changelog

All notable changes to this project will be documented in this file.

## [1.0.0] - 2025-04-20
### Added
- Implemented all six creational design patterns:
  - Simple Factory for Vehicle types
  - Factory Method for Payment processors
  - Abstract Factory for cross-platform UI
  - Builder for customizable Pizza creation
  - Prototype for Shape cloning
  - Singleton for DatabaseConnection
- Added README with pattern justifications
- Wrote unit tests for each pattern under `/tests`
- Integrated `pytest-cov` for test coverage reporting

### Fixed
- #15: Made Singleton thread-safe with locking mechanism
- #18: Added input validation for `add_toppings(None)` in Builder

### Changed
- Enhanced Prototype to use `copy.deepcopy()` for complex cloning

### Known Issues
- Test case on MacOSFactory intermittently fails on CI (tracking in #22)

---
