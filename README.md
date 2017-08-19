<p align="center">
  <img src="https://github.com/joshwcomeau/new-component/blob/master/docs/logo@2x.png?raw=true" width="285" height="285" alt="new-component logo">
  <br>
  <a href="https://www.npmjs.org/package/new-component"><img src="https://img.shields.io/npm/v/new-component.svg?style=flat" alt="npm"></a>
</p>

# `new-component`
### Simple, customizable utility for adding new React components to your project.

<img src="https://github.com/joshwcomeau/new-component/blob/master/docs/divider@2x.png?raw=true" width="888" height="100" role="presentation">

Anyone else sick of writing the same component boilerplate, over and over?

This project is a globally-installable CLI for adding new React components. It's dead simple to use, and requires no configuration, although it's easy to customize it to fit your project's coding style.

<br />

## Features
- Simple CLI interface for adding Component, PureComponent, or Stateless Functional components.
- Uses [Prettier](https://github.com/prettier/prettier) to stylistically match the existing project.
- Offers global config, which can be overridden on a project-by-project basis.
- Colourful terminal output!


<br />

## Quickstart

Install via NPM:

```bash
# Using Yarn:
$ yarn global add new-component

# or, using NPM
$ npm i -g new-component
```

`cd` into your project's directory, and try creating a new component:

<p align="center">
  <img src="https://github.com/joshwcomeau/new-component/blob/master/docs/demo.gif?raw=true" width="888" height="369" alt="demo of CLI functionality">
</p>

Your project will now have a new directory at `src/components/Button`. This directory has two files:

```jsx
// `Button/index.js`
export { default } from './Button';
```

```jsx
// `Button/Button.js`
import React, { Component } from 'react';

class Button extends Component {
  render() {
    return <div />;
  }
}

export default Button;
```

> This structure might appear odd to you, with an `index.js` that points to a named file. I've found this to be an optimal way to set up components; the `index.js` allows you to `import` from the directory (eg. `import Button from 'components/Button'`), while having `Button.js` means that you're never lost in a sea of `index.js` files in your editor.
>
> This structure is not currently configurable, but I'm happy to consider implementing alternatives!


<br />

## Configuration

Configuration can be done through 3 different ways:

- Creating a global `.new-component-config.json` in your home directory (`~/.new-component-config.json`).
- Creating a local `.new-component-config.json` in your project's root directory.
- Command-line arguments.

The resulting values are merged, with command-line values overwriting local values, and local values overwriting global ones.



<br />

## API Reference

### Type

Control the type of component created:
- `class` for a traditional Component class (default),
- `pure-class` for a PureComponent class,
- `functional` for a stateless functional component.

Legacy `createClass` components are not supported, although support would be easy to add. Feel free to open an issue (or a PR!).

**Usage:**
Command line: `--type <value>` or `-t <value>`
JSON config: `{ "type": <value> }`


### Directory

Controls the desired directory for the created component. Defaults to `src/components`

Legacy `createClass` components are not supported, although support would be easy to add. Feel free to open an issue (or a PR!).

**Usage:**
Command line: `--dir <value>` or `-d <value>`
JSON config: `{ "dir": <value> }`

### File Extension

Controls the file extension for the created components. Can be either `js` (default) or `jsx`.

**Usage:**
Command line: `--extension <value>` or `-x <value>`
JSON config: `{ "extension": <value> }`

### Prettier Config

Delegate settings to Prettier, so that your new component is formatted as you'd like. Defaults to Prettier defaults.

For a full list of options, see the [Prettier docs](https://github.com/prettier/prettier#options).

**Usage:**
Command line: N/A (Prettier config is only controllable through JSON)
JSON config: `{ "prettierConfig": { "key": "value" } }`

**Example:**

```js
{
  "prettierConfig": {
    "singleQuote": true,
    "semi": false,
  }
}
```


## Platform Support
This has only been tested in MacOS. I think it'd work fine in linux, but I haven't tested it. Windows is a big question mark (would welcome contribution here!).


## TODO

This is a brand new thing! I'd like to add more functionality:

- Built-in support for common style tools (CSS modules, Aphrodite, styled-components, etc).
- Better error messaging, more edge-case support
- Editor integrations :o