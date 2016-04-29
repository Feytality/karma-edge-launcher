# karma-ie-launcher

[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/nicolasmccurdy/karma-edge-launcher)
 [![npm version](https://img.shields.io/npm/v/karma-edge-launcher.svg?style=flat-square)](https://www.npmjs.com/package/karma-edge-launcher) [![npm downloads](https://img.shields.io/npm/dm/karma-edge-launcher.svg?style=flat-square)](https://www.npmjs.com/package/karma-edge-launcher)

[![Build Status](https://img.shields.io/travis/nicolasmccurdy/karma-edge-launcher/master.svg?style=flat-square)](https://travis-ci.org/nicolasmccurdy/karma-edge-launcher) [![Dependency Status](https://img.shields.io/david/nicolasmccurdy/karma-edge-launcher.svg?style=flat-square)](https://david-dm.org/nicolasmccurdy/karma-edge-launcher) [![devDependency Status](https://img.shields.io/david/dev/nicolasmccurdy/karma-edge-launcher.svg?style=flat-square)](https://david-dm.org/nicolasmccurdy/karma-edge-launcher#info=devDependencies)

> Launcher for Internet Explorer.

## Installation

The easiest way is to keep `karma-ie-launcher` as a devDependency, by running

```bash
npm install karma-ie-launcher --save-dev
```

## Configuration
```js
// karma.conf.js
module.exports = function(config) {
  config.set({
    browsers: ['IE']
  });
};
```

You can pass list of browsers as a CLI argument too:
```bash
karma start --browsers IE
```

### Running IE in "No add-ons mode"

Please note that since **v0.2.0** default behaviour of launching Internet Explorer has changed.
Now it runs using system-wide configuration (uses same settings as if you would run it manually) but prior to **v0.2.0** it was spawned with `-extoff` flag set explicitly, so all extensions were disabled.

If you expect the same behaviour as it was before **v0.2.0**, Karma configuration should be slightly changed:
- create new `customLauncher` configuration (`IE_no_addons` is used in an example below) with custom flags (in our case it is `-extoff` only)
- browser `IE` in `browsers` field should be replaced with your new custom launcher name
```js
  browsers: ['IE_no_addons'],
  customLaunchers: {
    IE_no_addons: {
      base:  'IE',
      flags: ['-extoff']
    }
  }
```

See [IE Command-Line Options] on MSDN.

----

For more information on Karma see the [homepage].


[homepage]: http://karma-runner.github.com
[Specifying legacy document modes]: http://msdn.microsoft.com/en-us/library/ie/jj676915(v=vs.85).aspx
[IE Command-Line Options]: https://msdn.microsoft.com/en-us/library/hh826025(v=vs.85).aspx
