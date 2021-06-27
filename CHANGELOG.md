# Changelog

## v1.1.0
**NOTE**: this release of in-toto drops supports for Python 2.7.
This is because Python 2.7 was marked [end-of-life](
https://www.python.org/dev/peps/pep-0373/) in January of 2020, and
since then several of in-toto's direct and transitive dependencies have stopped
supporting Python 2.7.

### Added
* SPDX License identifiers and copyright information (#440)
* Aditya Sirish (@adityasaky) as a maintainer (#443)

### Changed
* PyPI development status from `Beta` to `Production/Stable` (#447)
* Santiago Torres-Arias's (@SantiagoTorres) email to reflect Purdue affiliation
  (#446)
* Debian downstream release metadata (#437)
* Bump dependency: cryptography (#442)

### Removed
* Dropped support for Python 2.7 (#438)


## v1.0.1
**NOTE**: this will be the final release of in-toto that supports Python 2.7.
This is because Python 2.7 was marked [end-of-life](
https://www.python.org/dev/peps/pep-0373/) in January of 2020, and
since then several of in-toto's direct and transitive dependencies have stopped
supporting Python 2.7.

### Added
* Python 3.9 in the CI test matrix (#419)
* Logo and other visual enhancements on readthedocs (#420, #428)
* Review of first evaluation period for 2021 roadmap (#421)

### Changed
* Switch to GitHub Actions for CI (#432)
* Switch to only running bandit on Python versions greater than 3.5 (#416)
* Debian downstream release metadata (#418)
* Bump tested dependencies: cffi (#415, #427), cryptography (#424, #429),
  securesystemslib (#430, #431), iso8601 (#423) **NOTE**: the latest version of
  cryptography is no longer used on Python 2, as that is not supported.

### Removed
* Dropped support for Python 3.5 (#419)


## in-toto v1.0.0

### Added
* '-P/--password' (prompt) cli argument for in-toto-run/in-toto-record (#402)
* in-toto-run link command timeout setting (#367)
* API and usage documentation for cryptographic key handling with
  securesystemslib (#402, #408)
* Artifact recording exclude pattern documentation (#373, #405)
* Test key generation mixin (#402)
* 2021 roadmap document (#381)

### Changed
* Move 'settings' docs to new 'configuration' section and make minor
  enhancements in structure and content (#405)
* Update tested dependencies (#377, #383, #384, #386, #389, #390,  #394, #397,
  #398, #400, #404, #406, #409, #410, #411)
* Debian downstream release metadata (#382)

### Removed
* 'util' crypto module in favor of securesystemslib key interfaces (#402)
* Obsolete coveralls.io API call in Travis test builds (#399)

### Fixed
* Minor docs issues (#396, #385, #395)
* pylint 2.6.0 (#387) and lgtm.com (#379) warnings


## in-toto v0.5.0

* Docs: Major CLI and API documentation overhaul and release (#341, #369)
* Bugfix: Use kwargs in in-toto-run to fix lstrip-paths bug (#340)
* Feature: Add option to specify target directory for generated metadata (#364)
* Tests: Add Python 3.8 to tested versions (#339)
* Tests: Add tmp dir and gpg key test mixins (#345)
* Tests: Use constant from securesystemslib to detect GPG in tests (#352)
* Tests: Enhance test suite feedback on Windows (#368)
* Dependencies: Misc updates (#342, #346, #349, #350, #353, #354, #356, #358,
  #359,  #362, #363, #366)

## in-toto v0.4.2

* Drop custom OpenPGP subpackage and subprocess module and instead use the
  ones provided by securesystemslib, which are based on the in-toto
  implementation and receive continued support from a larger community (#325)
  - A race condition that caused tests to sporadically fail was already fixed
    in securesystemslib and is now also available to in-toto (#282,
    secure-systems-lab/securesystemslib#186)
* Add Sphinx boilerplate and update installation instructions (#298, #331)
* Update misc dependencies (#317, #318, #319, #320, #322, #323, #324, #326, #327, #328, #333, #335, #329)
* Update downstream debian metadata (#311, #334)

## in-toto v0.4.1

* Update securesystemslib dependency to v0.12.0 (#299)
* Add `--version` option to CLI tools (#310)
* Address linter warnings (#308)
* Update downstream debian metadata (#302, #305, #309)

## in-toto v0.4.0

* Add REQUIRE artifact rule support (#269, #280)
* Enhance OpenPGP key export and provide key expiration verification (#266, #288)
* Make transitive dependency PyNaCl optional for in-toto (#291)
* Improve automatic testing and code coverage measurement (#295) as well
  as static analysis with pylint (#279, #296)
* Update repository metadata
  - Add initial 1-year roadmap (#268)
  - Revise dependency handling for monitoring and library compatibility (#294)
  - Update maintainers and contributor information (#283, #274, #297)
  - Enhance source distribution configs and include tests and other metadata,
    relevant to downstream packagers, with future source distributions (#290)

## in-toto v0.3.0

* Re-factor rule verification engine and fix for a false-reject on very specific layouts (#262)
* Add support for duplicate standard streams (#252)
* Enhance support for Summary link naming (i.e., better sublayout verification, #256)
* Improve rule verification messages (#243)
* Small fixes for OpenPGP parsing functions (#255)
* Properly verify self-signature and signature binding signatures upon export (#257)
* Add lstrip-paths parameter (as an enhancement/replacement for basepath) (#250)
* Fix a bug where multiple PGP subkeys could count towards the threshold (#251)
* Fix a bug where RSA signatures wouldn't be sufficiently padded and a signature would be erroneously-rejected #170
* Change license to Apache

## in-toto v0.2.3

* Add common interface for Python's subprocess module
* Add Python 3.7 support
* Drop Python 3.3 support
* Add windows support
* Add AppVeyor testing (windows)
* Add optional line ending normalization when hashing artifacts (windows)
* Add optional compact json representation for metadata
* Make exclude filter behavior match gitignore when recording artifacts
* Make cwd recording optional when creating link metadata
* Add a substitution layer to support parameter substitution upon verification
* Improve gpg support
* Add full support for ed25519 keys and add optional key type parameter
* Fix bug in rule verification (https://github.com/in-toto/in-toto/pull/204)


## in-toto v0.2.2

* Add support for gpg signing subkeys.
* Drop strict requirement on securesystemslib 0.10.
* Command line tool changes:
    - Add a --base-path parameter to in-toto record and in-toto run
    - in-toto-record now follows symbolic links
* Fixed typo in exception messages
* Adds support for sublayout namespacing (for in-toto spec 0.9 compliance)
* Path prefix is normalized during in-toto verification:
    - Paths such as foo//bar match with foo/bar.
* Dropped obsolete SettingsError


## in-toto v0.2.1

* Model changes
  - Add metablock validators
  - Add abstract class for layout steps and inspections
  - Disallow passing command string to step and inspection constructor
  - Add custom `__repr__` for step and inspection objects
  - Add layout creation convenience methods
* Command Line tool changes
  - Add missing shebangs
  - Enhance help messages
  - Fix argparse bug for required subcommand in in-toto-record
  - Rename short option to record streams in in-toto-run
* Fix gpg hashing algorithm name
* Add layout creation example document
* Refactor logging and user feedback
* Rename artifact_rules module to rulelib and add convenience methods


## in-toto v0.2.0

* Fix link metadata bug in in_toto_mock
* Add support for GPG signing and verification of layout and link metadata
* Add support for Python 3.4, 3.5 and 3.6
* Refactor signature and threshold verification in final product verification
  so that not every signature on a given layout needs to be valid, as long as
  every signature for which a key is passed is valid, and at least one key is
  passed. Furthermore, not all imported links need need to carry an authorized
  and valid signature, as as long as there are enough links with an authorized
  and valid signature for any given step. Links with unauthorized signatures or
  invalid signatures are ignored
* Remove canonicaljson dependency and use securesystemslib's canonicaljson
  encoding
* Refactor order of positional arguments in in-toto-record command line tool
* Add linters (pylint and bandit) and fix linting errors (e.g.: indentation
  and unused variables and imports)
* Add schemas for in-toto specific crypto-related metadata formats
* Improve testing code coverage to 100%
* Add debian directory required to create a debian package
* Add .editorconfig and GitHub issue and pull request templates,
  ACKNOWLEDGEMENTS.md, CODE-OF-CONDUCT.md, GOVERNANCE.md, MAINTAINERS.txt and
  passing core infrastructure best practice badge, add "Security Issues and
  Bugs" and "Instructions for Contributors" section in README.md


## in-toto v0.1.1
* Initial pre-release
