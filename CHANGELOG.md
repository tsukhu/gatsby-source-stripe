# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## Unreleased
- Nada

## [2.2.2](https://github.com/njosefbeck/gatsby-source-stripe/compare/v2.2.1...v2.2.2) - 2019-04-13
- Fix file capitalization issue.

## [2.2.1](https://github.com/njosefbeck/gatsby-source-stripe/compare/v2.2.0...v2.2.1) - 2019-04-13
- Fix issue where need an index.js file, even if blank, so that Gatsby can find the plugin.

## [2.2.0](https://github.com/njosefbeck/gatsby-source-stripe/compare/v2.1.9...v2.2.0) - 2019-04-13
- Add ESLint and prettier configuration & dependencies.
- Fix bootstrap progressing without awaiting file downloads.
- Fix cached Gatsby File nodes being deleted after development server restart.
- Refactor LocalFile.js to improve readability. (Thanks @Francesco-Lanciana !)
- Add the ability to remove Authorization headers from any HTTP request made when fetching files not hosted on Stripe. (Thanks @Francesco-Lanciana !)
- Remove babel-compiled files from .gitignore.
- Add .npmignore.
- Add engines field to package.json. This plugin only works in versions of Node >= 10.13.0.
- Update package.json scripts for properly building plugin for publishing.
- Add .npmrc to enforce exact versions when adding new packages to the project.
- Add coding guidelines section to CONTRIBUTING.md.
- Update @babel/cli from 7.2.3 to 7.4.3.
- Update @babel/core from 7.4.0 to 7.4.3.
- Update @babel/preset-env from 7.4.2 to 7.4.3.
- Update eslint-plugin-import from [2.16.0 to 2.17.0](https://github.com/benmosher/eslint-plugin-import/blob/master/CHANGELOG.md).
- Update gatsby-source-filesystem from [2.0.28 to 2.0.29](https://github.com/gatsbyjs/gatsby/blob/master/packages/gatsby-source-filesystem/CHANGELOG.md).
- Update prettier from [1.16.4 to 1.17.0](https://prettier.io/blog/2019/04/12/1.17.0.html).

## [2.1.9](https://github.com/njosefbeck/gatsby-source-stripe/compare/v2.1.6...v2.1.9) - 2019-03-27
### Changed
- Update stripe from [6.20.0 to 6.28.0](https://github.com/stripe/stripe-node/blob/master/CHANGELOG.md).
- Update gatsby-source-filesystem from [2.0.16 to 2.0.28](https://github.com/gatsbyjs/gatsby/blob/master/packages/gatsby-source-filesystem/CHANGELOG.md).
- Update @babel/cli from 7.2.0 to 7.2.3.
- Update @babel/core from 7.2.2 to 7.4.0.
- Update @babel/preset-env from 7.2.2 to 7.4.0.

## [2.1.7](https://github.com/njosefbeck/gatsby-source-stripe/compare/v2.1.6...v2.1.7) - 2019-02-11
### Changed
- Update @babel/preset-env from [7.2.3 to 7.3.1](https://github.com/babel/babel/releases).
- Update gatsby-source-filesystem from [2.0.16 to 2.0.20](https://github.com/gatsbyjs/gatsby/blob/master/packages/gatsby-source-filesystem/CHANGELOG.md).
- Update stripe from [6.20.0 to 6.23.1](https://github.com/stripe/stripe-node/blob/master/CHANGELOG.md).

## [2.1.6](https://github.com/njosefbeck/gatsby-source-stripe/compare/v2.1.5...v2.1.6) - 2019-01-14
### Changed
- Add information to README about using restricted API keys

## [2.1.5](https://github.com/njosefbeck/gatsby-source-stripe/compare/v2.1.4...v2.1.5) - 2019-01-14
### Changed
- Fix File-breaking typo (Thanks @brxck!)

## [2.1.4](https://github.com/njosefbeck/gatsby-source-stripe/compare/v2.1.3...v2.1.4) - 2019-01-12
### Changed
- Update [README](README.md) with the following:
    - Add links to the newly added CONTRIBUTING and CODE OF CONDUCT documents
    - Add caveat to file downloading section about using Checkout's beta
- Refinements to file downloading feature (Thanks @brxck for your contributions!)
    - Remove no longer needed dummy password
    - Check node type before attempting download
    - Update downloading for iterable File nodes
    - Correct query for localFiles
- Update gatsby-source-filesystem from [2.0.11 to 2.0.16](https://github.com/gatsbyjs/gatsby/blob/master/packages/gatsby-source-filesystem/CHANGELOG.md).

## [2.1.3](https://github.com/njosefbeck/gatsby-source-stripe/compare/v2.1.2...v2.1.3) - 2019-01-08
### Changed
- Update stripe from [6.18.0 to 6.20.0](https://github.com/stripe/stripe-node/blob/master/CHANGELOG.md).
- Update gatsby-source-filesystem from [2.0.11 to 2.0.12](https://github.com/gatsbyjs/gatsby/blob/master/packages/gatsby-source-filesystem/CHANGELOG.md).
- Update @babel/cli from 7.2.0 to 7.2.3.
- Update @babel/core from 7.2.0 to 7.2.2.
- Update @babel/node from 7.2.0 to 7.2.2.
- Update @babel/preset-env from 7.2.0 to 7.2.3.
- Add [code of conduct](CODE_OF_CONDUCT.md) file.
- Add [contributing](CONTRIBUTING.md) file.
- Add [issue template](ISSUE_TEMPLATE.md) file.

## [2.1.2](https://github.com/njosefbeck/gatsby-source-stripe/compare/v2.1.0...v2.1.2) - 2018-12-09
### Changed
- Update project dependencies, including stripe, which fixes issue #11.
- Change README and inline code comments to reflect update (Stripe Files are now iterable!).

## [2.1.0](https://github.com/njosefbeck/gatsby-source-stripe/compare/v2.0.5...v2.1.0) - 2018-12-06
### Changed
- Add support for downloading File objects associated with File objects, and images on Sku and Product objects. This will enable images to be processed by gatsby-transformer-sharp and used with gatsby-image. Read the updated README for more information. Thanks to @brxck for this AWESOME update.
- Update peer dependency for Gatsby to >= 2.0.15. This is necessary since the plugin uses "createContentDigest", which didn't exist in versions prior to 2.0.15. Peer dependency information can be found in `package.json` and in the README.
- Update project dependencies to latest versions.

## [2.0.5](https://github.com/njosefbeck/gatsby-source-stripe/compare/v2.0.0...v2.0.5) - 2018-11-20
### Changed
- Fix generated file to accurately reflect StripeObject.js
- Add babel-transpiled files back to version control to ensure they are part of npm package when installed by users.
- Moved dependencies to devDependencies to avoid dependency pollution.

## [2.0.0](https://github.com/njosefbeck/gatsby-source-stripe/compare/v1.2.1...v2.0.0) - 2018-11-18
### Changed
- This release contains a number of breaking changes.
  - Due to the way we're handling auto-pagination, you must use Node v.10 or higher when using this version of the plugin.
  - When adding Stripe objects to the objects array in `gatsby-config.js`, you must use the object types listed in the README. Thus, the type names have changed.
- Re-write plugin to incorporate [stripe-node](https://github.com/stripe/stripe-node) auto-pagination.
- Update README to include more information about how to use the plugin.
- Update plugin implementation to bring it fully up to date with Stripe API version 2018-11-08. This involves adding some new object types (ex: TopUp, TerminalLocation), and renaming other objects (fileUploads becomes File).
- Add plugin information for the Stripe library as recommended [here](https://github.com/stripe/stripe-node#writing-a-plugin).

## [1.2.1](https://github.com/njosefbeck/gatsby-source-stripe/compare/v1.2.0...v1.2.1) - 2018-11-02
### Changed
- Update stripe dependency to 6.13.0.

## 1.2.0 - 2018-10-09
### Changed
- Add CHANGELOG.
- Fix issue where pagination wouldn't stop when calling Stripe methods. Fixed by @raae.
- Add gatsby v1+ as peer dependency as recommended [here](https://github.com/gatsbyjs/gatsby/blob/master/docs/docs/migrating-from-v1-to-v2.md#for-plugin-maintainers).
- Rename `boundActionCreators` to `actions` as part of [Gatsby v2 migration](https://github.com/gatsbyjs/gatsby/blob/master/docs/docs/migrating-from-v1-to-v2.md#rename-boundactioncreators-to-actions).
- Update [Stripe Node.js Library](https://www.npmjs.com/package/stripe) from 6.8.0 to 6.12.1.