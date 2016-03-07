# grunt-vegas-assets-copy v0.0.1

> Copy files and folders for vegas-cmf assets


## Getting Started

```shell
npm install grunt-vegas-assets-copy --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-vegas-assets-copy');
```

## Copy task
_Run this task with the `grunt vegas-assets-copy` command._

Task targets, files and options may be specified according to the grunt [Configuring tasks](http://gruntjs.com/configuring-tasks) guide.
### Options
[grunt-contrib-copy Documentation](https://github.com/gruntjs/grunt-contrib-copy).

#### Truncate options usage example

```js
copy: {
  main: {
    files: [
      {
        expand: true,
        cwd_truncate: true,
        cwd: 'vendor/vegas-cmf',
        src: '*/assets/**',
        dest: 'public/assets/'
      },
    ],
  },
},
```

If you want to avoid overwriting files, please define a filter field.

#### Truncate with file filter

```js
copy: {
  main: {
    files: [
      {
        expand: true,
        cwd_truncate: true,
        cwd: 'vendor/vegas-cmf',
        src: '*/assets/**',
        dest: 'public/assets/',
        filter: function (filepath) {
          var path = require('path');
          var dest = path.join(grunt.config('copy.main.dest'), path.basename(filepath));
          return !(grunt.file.exists(dest));
        }
      },
    ],
  },
},
```
