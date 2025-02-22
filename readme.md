# About

Echoes a `package.json` script's commandline before Yarn executes it. This patches the design decision in Yarn v2 to
omit the commandline echo that traditionally occurs before execution. An official setting to restore this behavior
natively will not be implemented: see [#1215](https://github.com/yarnpkg/berry/issues/1215).

## Discretion

The main motivation for this design decision in Yarn v2 is compatibility with tools that parse console output from other
tools: test report scanners, JSON readers, etc. Using `yarn-plugin-echo-execute` is thus not recommended if your project
includes tools that parse console output. If such a tool fails while this plugin is enabled, verify that it isn't the
cause before contacting the Yarn developers for support.

# Acquiring

Since updates are rare, the script is simply built locally and [committed](./bundles/@yarnpkg/plugin-echo-execute.js).
Install it in your project using either of the following:

- `yarn plugin import https://yarnplugins.com/echo-execute` (recommended)
- `yarn plugin import https://raw.githubusercontent.com/leaumar/yarn-plugin-echo-execute/master/bundles/%40yarnpkg/plugin-echo-execute.js`

## Building

1. `yarn install`
2. `yarn build`
3. run `yarn plugin import path/to/./bundles/@yarnpkg/plugin-echo-execute.js` in your target project(s)
4. profit

# Maintaining

1. `yarn install`
2. make changes
3. `yarn build`
4. commit updated sources and artifact
5. add a `release-n` tag
6. party
