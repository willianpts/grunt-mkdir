# grunt-mkdir

> Create directories with Grunt.

[![Build Status](https://travis-ci.org/rubenv/grunt-mkdir.png?branch=master)](https://travis-ci.org/rubenv/grunt-mkdir)

## Getting Started
This plugin requires Grunt `~0.4.0`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-mkdir --save-dev
```

One the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-mkdir');
```

## The "mkdir" task

### Overview
In your project's Gruntfile, add a section named `mkdir` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  mkdir: {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      // Target-specific options go here.
    },
  },
})
```

Note that we cannot use the standard `files` section in the configuration, as that one is filtered to only include existing files.

### Options

#### options.create
Type: `Array`

An array of folder names to create.

#### options.mode
Type: `Number`

The mode of the file to create. Defaults to `0777 & (~process.umask())`.

#### options.user
Type: `String`

The username or uid of the desired file owner. Defaults to current user.
Please note that it only works with sudo privileges.

#### options.group
Type: `String`

The groupname or gid of the desired file group. Defaults to user primary group.
This may not work if your current user is not in the target group. If that's the case, use sudo.

### Usage Examples

#### Simple usage
The following example will create a `tmp` folder that is only accessible to the owner:

```js
grunt.initConfig({
  mkdir: {
    all: {
      options: {
        mode: 0700,
        create: ['tmp']
      },
    },
  },
})
```

#### Group usage
This time, we'll give write permissions to the test group:

```js
grunt.initConfig({
  mkdir: {
    all: {
      options: {
        mode: 0770,
        group: 'test',
        create: ['tmp_group']
      },
    },
  },
})
```

#### Fileowner
Now let's change the fileowner.
Note: run grunt with sudo privileges.

```js
grunt.initConfig({
  mkdir: {
    all: {
      options: {
        user: 'someuser',
        create: ['tmp_someuser']
      },
    },
  },
})
```

#### Multiple and recursive folders
You can create multiple folders and even recursively create folders:

```js
grunt.initConfig({
  mkdir: {
    all: {
      options: {
        create: ['tmp', 'test/very/deep/folder']
      },
    },
  },
})
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History

* 2013-03-11   v0.1.0   Initial release.
