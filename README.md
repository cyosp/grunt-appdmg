# grunt-appdmg [![Build Status](https://travis-ci.org/rakuten-frontend/grunt-appdmg.svg?branch=master)](https://travis-ci.org/rakuten-frontend/grunt-appdmg)

> Grunt plugin for generating Mac OSX DMG-images

## Overview
[node-appdmg](https://github.com/LinusU/node-appdmg) is an awesome command line tool to generate Mac disk images.
This grunt plugin wraps the node-appdmg and executes it using Gruntfile.  
You can use Grunt template strings in the appdmg config, like: `title: '<%= pkg.name %>'`.

**Note:**  
grunt-appdmg works on **Mac OS X only** due to the node-appdmg limitation.

## Getting Started
If you are new to Grunt, you will find a lot of answers to your questions in their [getting started guide](http://gruntjs.com/getting-started).  
Install this plugin with this command:

```shell
npm install grunt-appdmg --save-dev
```

Once the plugin has been installed, it may be enabled inside your "Gruntfile.js" with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-appdmg');
```

## The "appdmg" task

### Options
See the [JSON Specification](https://github.com/LinusU/node-appdmg#json-specification) of node-appdmg.
Options except for **configFile** follow the spec.

#### configFile
Type: 'String'  
Default: `.tmp/appdmg/config.json`

Path to the temporary config file for appdmg task.

### Example config
In your project's Gruntfile, add a section named `appdmg` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  appdmg: {
    options: {
      title: 'Title of DMG',
      icon: 'path/to/icon.icns',
      background: 'path/to/background.png',
      'icon-size': 80,
      contents: [
        {x: 448, y: 344, type: 'link', path: '/Applications'},
        {x: 192, y: 344, type: 'file', path: 'path/to/your-app.app'},
        {x: 512, y: 128, type: 'file', path: 'path/to/extra-file.txt'}
      ]
    },
    target: {
      dest: 'your-app.dmg'
    }
  }
});
```

## License
Copyright (c) 2014 Rakuten, Inc. Licensed under the [MIT License](http://opensource.org/licenses/MIT).
