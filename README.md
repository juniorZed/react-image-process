# :rocket: react-image-process

[![Build Status](https://travis-ci.org/yohangz/packer-cli.svg?branch=master)](https://travis-ci.org/yohangz/packer-cli)
[![MIT](https://img.shields.io/badge/license-MIT-blue.svg?style=flat)](https://github.com/yohangz/packer-cli/blob/master/LICENSE)
[![NPM VERSION](https://badge.fury.io/js/packer-cli.svg)](https://badge.fury.io/js/packer-cli)

> React Package for Image Processing

## :book: Table of Contents
  <!-- START doctoc generated TOC please keep comment here to allow auto update -->
  <!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

  - [Usage](#mag_right-basic-usage)
  - [Standalone Usage](#gear-standalone-usage)
  - [Project Structure](#open_file_folder_project_structure)
  - [Build Configuration](#hammer_and_pick-build-configuration)
  - [Contributions](#seedling-contributions)

  <!-- END doctoc generated TOC please keep comment here to allow auto update -->

## :mag_right: Usage

```sh
# Run project on watch mode
npm run watch

# Production build
npm run build

# Run Style and script lint tasks
npm run lint

# Run style lint task
npm run lint:style

# Run script lint task
npm run lint:script

# Run auto format source task
npm run format

# Run unit test suite on development envrionemnt watch mode
npm run test

# Run unit test suite with coverage on development envrionemnt watch mode
npm run test:coverage

# Run unit test suite on continues integration environment mode
npm run test:ci

# Run unit test suite with coverage mode on continues integration environment mode
npm run test:coverage:ci

# Bump package version and push updated package config
npm version major|minor|patch

# Build project and publish to NPM
npm run release
```

## :gear: Standalone Usage

You can also use packer CLI standalone on any packer compliant project to customize the NPM scripts generated.

```text
Usage: packer [--version | -v] | [--help | -h] | <command>[<args>]

  Arguments supported with all commands

  + Logging flags
    [--trace]          set console log level to trace
    [--info]           set console log level to information
    [--warn]           set console log level to warning
    [--error]          set console log level to error
    [--silent]         set console log level to silent

  + Other Flags
    [--config | -c]    dynamic packer config path

  Generate a new library project via packer

  generate | g <project name>
    [--skipInstall | -sk]   skip dependency install after project

  These are packer commands can be used on generated project
    build | b                trigger build
      [--perf | -P]          execute build task with rollup performance monitoring
    watch | w                trigger serve on watch mode
    test | t                 execute project test suite
      [--watch | -W]         execute test on watch mode
      [--coverage | -C]      execute test suite with coverage
    clean | c                clean project build artifacts and temporary files generated
    lint | l                 execute lint for project source
      [--style | -sc]        execute only style lint
      [--script | -sr]       execute only script lint
    format | f               auto format project source
```


## :open_file_folder: Project Structure

```
.
├── /.packer/                   # Packer build associated helper templates directory.
│   ├── .banne.hbs              # Distribution script top banner comment template.
│   └── .bin.hbs                # Distribution script bin file template used in CLI projects.
├── /.tmp/                      # Packer temporary artifacts and cache directory.
├── /__mocks__/                 # Jest mock script directory. Optional: applicable when test framework is 'jest'.
├── /coverage/                  # Coverage directory generated when running unit test on coverage mode.
├── /demo/                      # Demo source content. Optional: applicable when watch source serve is enabled.
│   ├── /build/                 # Build demo pages/scripts and assets.
│   ├── /helper/                # Watch and build demo helper script directory.
│   │   ├── require.min.js      # RequireJS static artifact. Optional: applicable when build mode is 'browser' & bundle format is 'amd'.
│   │   └── system.min.js       # SystemJS static artifact. Optional: applicable when build mode is 'browser' & bundle format is 'system'.
│   └── /watch/                 # Watch demo pages/scripts and assets.
├── /helpers/                   # Unit test helper script files. Optional: applicable only when framework is 'mocha' or 'jasmine' & test environment is not 'browser'.
├── /dist/                      # Compiled distribution artifacts directory (Generated by build task).
│   ├── /bundle                 # Directory containing main bundled (umd | amd | iife | system | ejs | esm) artifact depending on bundle build type.
│   ├── /fesm5                  # Directory containing FESM5 artifact. Optional: applicable only when es5 build is enabled.
│   ├── /fesmnext               # Directory containing FESMNEXT artifact. Optional: applicable only when esnext build is enabled.
│   ├── /styles                 # Directory containing compiled style sheets. Optional: applicable only when style support is enabled.
│   ├── /typings                # Source type definition files generated by typescript compiler. Optional: applicable only when script preprocessor is 'typescript'.
│   ├── /LICENSE                # Project license agreement file copied from project root. Optional: applicable only when included in copy files configuration.
│   ├── /package.json           # Dynamically generated Package.json file with publish artifact specific metadata.
│   └── /README.md              # Package documentation markup file copied from project root. Optional: applicable only when included in copy files configuration.
├── /node_modules/              # Node modules directory
├── /src/                       # Project source directory
│   ├── /**                     # Contain any sub source and test files and directories.
│   └── /index.{ts,js}          # Library entry point file configured in packer config. Exports in this file are exposed by bundled build artifact.
├── .babelrc                    # Babel configuration file (https://babeljs.io/).
├── .editorconfig               # Define and maintain consistent coding styles between different editors and IDE's (https://editorconfig.org/).
├── .eslintrc.yml               # ESLint configuration (https://eslint.org/). Optional: applicable only when script preprecessor is 'none'.
├── .gitignore                  # Contains files to be ignored from git repository (https://git-scm.com/docs/gitignore).
├── .packerrc.js                # Packer configuration file containing project build options (https://github.com/yohangz/packer-cli).
├── .stylelintrc.json           # Style lint configuration (https://stylelint.io). Optional: applicable only when style support is enabled.
├── .travis.yml                 # Travis CI configuration file (https://travis-ci.com/).
├── jasmine.json                # Jasmine test framework configuration file (https://jasmine.github.io/). Optional: applicable only when test framework is 'jasmine' & test environment is 'browser'.
├── jest.config.js              # Jest test framework configuration file (https://jestjs.io/). Optional: applicable only when test framework is 'jest'.
├── karma.conf.js               # Karma unit test runner configuration (https://karma-runner.github.io). Optional: applicable only when test environment is 'browser' & test framework is either 'mocha' or 'jasmine'.
├── LICENSE                     # License agreement file.
├── mocha.opts                  # Mocha test framework CLI configuration options file (https://mochajs.org/). Optional: applicable when test framework is 'mocha' & test environment is 'browser'.
├── package.json                # Node package configuration file (https://www.npmjs.com/).
├── postcss.config.js           # PostCSS configuration file (https://postcss.org/). Optional: applicable only when style support is enabled.
├── README.md                   # Project documentation markup file.
├── tsconfig.json               # Base typescript compiler options and configuration file (https://www.typescriptlang.org/). Optional: only applicable when script preprocessor is 'typescript'.
├── tsconfig.test.json          # Typescript compiler options and configuration file by test frameworks (https://www.typescriptlang.org/). Optional: applicable only when test framework is either 'mocha' or 'jasmine' & build mode is not 'browser' &  script preprocessor is 'typescript'.
├── tslint.json                 # TSlint configuration file (https://palantir.github.io/tslint/). Optional: applicable only when script proprocessor is 'typescript'.
└── yarn.lock                   # Yarn package lock file (https://yarnpkg.com). Optional: applicable only when package manager is 'yarn'.
```

## :hammer_and_pick: Build Configuration

Build configuration can be updated after project generation via ``.packerrc.js``.

```js
/**
 * Packer base configuration object.
 */
module.exports = {
  /**
   * Extend with packer base config
   * @type {string}
   * @default '~/packer-cli/resources/static/.packerrc.base.js'
   */
  extend: '~/packer-cli/resources/static/.packerrc.base.js',

  /**
   * Entry source file.
   * @type {string}
   * @default 'index.js'
   */
  entry: 'index.js',

  /**
   * Source directory
   * @type {string}
   * @default 'src'
   */
  source: 'src',

  /**
   * Build artifact output directory
   * @type {string}
   * @default 'dist'
   */
  dist: 'dist',

  /**
   * Watch and build temporary file directory
   * @type {string}
   * @default '.tmp'
   */
  tmp: '.tmp',

  /**
   * Packer compiler options
   */
  compiler: {

    /**
     * Dependency map mode option in target package.json file.
     * - 'cross-map-peer-dependency' : Map project dependencies to target peerDependencies
     * - 'cross-map-dependency' : Map project peerDependencies to target dependencies
     * - 'map-dependency' : Map project dependencies to target dependencies
     * - 'map-peer-dependency' : Map project peer dependencies to target peerDependencies
     * - 'all' - Map both peerDependencies and dependencies to target peerDependencies and dependencies
     * @type {string}
     * @default 'cross-map-peer-dependency'
     */
    dependencyMapMode: 'cross-map-peer-dependency',

    /**
     * Specified package fields will be copied to target package.json file.
     * @type {Array<string>}
     * @default [ 'name', 'version', 'description', 'keywords', 'author', 'repository', 'license', 'bugs', 'homepage' ]
     */
    packageFieldsToCopy: [
      'name',
      'version',
      'description',
      'keywords',
      'author',
      'repository',
      'license',
      'bugs',
      'homepage'
    ],

    /**
     * If true, a separate sourcemap file will be created. If inline, the sourcemap will be appended to
     * the resulting output file as a data URI.
     * @type {(boolean|string)}
     * @default true
     */
    sourceMap: true,

    /**
     * Custom rollup plugin extractor callback.
     * @callback customRollupPluginExtractorCallback
     * @param {string} buildType - 'bundle'|'es5'|'esnext'
     * @param {string} packerConfig - Packer configuration object.
     * @return {Array<{}>} Custom rollup plugin collection
     */

    /**
     * Extract custom rollup plugins to be executed while building the target artifacts.
     * @type {(null|customRollupPluginExtractorCallback)}
     */
    customRollupPluginExtractor: null,

    /**
     * Compile build target config.
     * @type {{}}
     * @default {}
     */
    build: {

      /**
       * Generate flat bundle minified build artifact.
       * @type {boolean}
       * @default true
       */
      bundleMin: true,

      /**
       * Generate flat es5 build artifact based on .babelrc es5 environment configuration.
       * @type {boolean}
       * @default false
       */
      es5: false,

      /**
       * Generate flat es5 minified build artifact.
       * @type {boolean}
       * @default false
       */
      es5Min: false,

      /**
       * Generate flat esnext build artifact based on .babelrc esnext environment configuration.
       * @type {boolean}
       * @default true
       */
      esnext: true,

      /**
       * Generate flat esnext minified build artifact.
       * @type {boolean}
       * @default true
       */
      esnextMin: true
    },

    /**
     * Library compile mode.
     * - 'browser' : Browser/NodeJS compliant module.
     * - 'node' : NodeJS only module.
     * - 'node-cli' : Node CLI module.
     * @type {string}
     * @default 'browser'
     */
    buildMode: 'browser',

    /**
     * Script compile configuration.
     * @type {{}}
     * @default {}
     */
    script: {

      /**
       * Script preprocessor.
       * - 'typescript' : use typescript preprocessor to transpile source.
       * - 'none': do not use any script preprocessor to transpile source.
       * @type {string}
       * @default 'none'
       */
      preprocessor: 'none',

      /**
       * Script required image compile configuration.
       * set false if not required to inline images
       * @type {({}|false)}
       * @default {}
       */
      image: {

        /**
         * Inline image if image size is less than or equal to specified limit.
         * @type {number}
         * @default 1000000
         */
        inlineLimit: 1000000,

        /**
         * Large image output directory within distribution directory.
         * @type {string}
         * @default 'images'
         */
        outDir: 'images'
      },
    },

    /**
     * Style compile configuration.
     * Set false if styles are not supported.
     * @type {({}|false)}
     * @default {}
     */
    style: {

      /**
       * Bundle styles inline within target build and inject to head at runtime.
       * @type {boolean}
       * @default false
       */
      inline: false,

      /**
       * Bundled style output directory path within distribution directory.
       * @type {string}
       * @default 'styles'
       */
      outDir: 'styles',

      /**
       * Style preprocessor
       * - 'scss' : SCSS style preprocessor.
       * - 'sass' : SASS style preprocessor.
       * - 'stylus' : Stylus style preprocessor.
       * - 'less' : LESS style preprocessor.
       * - 'none' : Do not use any style preprocessor.
       * @type {string}
       * @default 'none'
       */
      preprocessor: 'none',

      /**
       * Stylesheet required image compile configuration.
       * set false if not required to inline images
       * @type {({}|false)}
       * @default {}
       */
      image: {

        /**
         * Inline image if image size is less than or equal to specified limit.
         * @type {number}
         * @default 1000000
         */
        inlineLimit: 1000000,

        /**
         * Large image output directory within distribution directory.
         * @type {string}
         * @default 'images'
         */
        outDir: 'images'
      }
    },

    /**
     * Run bundle build tasks concurrently to improve performance if true
     * @type {boolean}
     * @default true
     */
    concurrentBuild: true,

    /**
     * Advance compiler options to override plugin configuration.
     * Caution! change only if you know what you are doing.
     * @type {{}}
     */
    advanced: {

      /**
       * Rollup plugins.
       * refer: https://rollupjs.org
       * @type {{}}
       */
      rollup: {

        /**
         * Override rollup build task input options.
         * refer: https://rollupjs.org inputOptions section.
         * @type {{}}
         */
        inputOptions: {},

        /**
         * Override rollup build task output options.
         * refer: https://rollupjs.org outputOptions section.
         * @type {{}}
         */
        outputOptions: {},

        /**
         * Override rollup watch task options.
         * refer: https://rollupjs.org watchOptions section.
         * @type {{}}
         */
        watchOptions: {},

        /**
         * Override rollup plugin options.
         * refer: https://rollupjs.org plugins section.
         * @type {{}}
         */
        pluginOptions: {

          /**
           * Override ignore import plugin options
           * refer: https://github.com/yohangz/rollup-plugin-ignore-import
           * @type {{}}
           */
          ignoreImport: {},

          /**
           * Override post css plugin options.
           * refer: https://github.com/egoist/rollup-plugin-postcss
           */
          postCss: {},

          /**
           * Override node resolve plugin options.
           * refer: https://github.com/rollup/rollup-plugin-node-resolve
           * @type {{}}
           */
          nodeResolve: {},

          /**
           * Override commonjs plugin options.
           * refer: https://github.com/rollup/rollup-plugin-commonjs
           * @type {{}}
           */
          commonjs: {},

          /**
           * Override json plugin options.
           * refer: https://github.com/rollup/rollup-plugin-json
           * @type {{}}
           */
          json: {},

          /**
           * Override globals plugin options.
           * refer: https://github.com/calvinmetcalf/rollup-plugin-node-globals
           * @type {{}}
           */
          globals: {},

          /**
           * Override babel plugin options.
           * refer: https://github.com/rollup/rollup-plugin-babel
           * @type {{}}
           */
          babel: {},

          /**
           * Override typescript plugin options.
           * refer: https://github.com/ezolenko/rollup-plugin-typescript2
           * @type {{}}
           */
          typescript: {},

          /**
           * Override replace plugin options.
           * refer: https://github.com/jetiny/rollup-plugin-re
           */
          replace: {},

          /**
           * Override image plugin options.
           * refer: https://github.com/alwaysonlinetxm/rollup-plugin-img
           * @type {{}}
           */
          image: {},

          /**
           * Override handlebars plugin options.
           * refer: https://github.com/yohangz/rollup-plugin-hbs
           * @type {{}}
           */
          handlebars: {},

          /**
           * Override filesize plugin options.
           * refer: https://github.com/ritz078/rollup-plugin-filesize
           * @type {{}}
           */
          filesize: {},

          /**
           * Override browserSync plugin options.
           * refer: https://github.com/4lejandrito/rollup-plugin-browsersync
           * All browser sync options are applicable: https://browsersync.io/docs/options
           * @type {{}}
           */
          browserSync: {}
        }
      },

      /**
       * Other plugins.
       */
      other: {

        /**
         * Override terser plugin options.
         * refer: https://github.com/terser-js/terser
         * @type {{}}
         */
        terser: {},

        /**
         * Override cssnano options.
         * refer: https://github.com/cssnano/cssnano
         * @type {{}}
         */
        cssnano: {}
      }
    }
  },

  /**
   * List of paths which contains static assets referenced in style sheets.
   * Paths should be relative to project root.
   * @type {Array<string>}
   * @default []
   */
  assetPaths: [
    'src/assets'
  ],

  /**
   * List of files paths to copy on build.
   * Paths should be relative to project root.
   * @type {Array<string>}
   * @default [ 'README.md', 'LICENSE' ]
   */
  copy: [
    'README.md',
    'LICENSE',
    'assets/**/{.*,*}'
  ],

  /**
   * Import paths to ignore with noop implementation.
   * Paths should be relative to project root.
   * @type {Array<string>}
   * @default []
   */
  ignore: [],

  /**
   * Custom rollup plugin extractor callback.
   * @callback pathReplaceCallback
   * @param {string} code - code segment
   * @param {string} id - file path/identifier.
   * @return {string} transformed code.
   */

  /**
   * Path Replace pattern object type.
   * @typedef {Object} PathReplacePattern
   * @property {(string|RegExp)} test - test expression or string.
   * @property {string} replace - string to replace the match.
   * @property {RegExp} match - regexp match with resolved path.
   * @property {(string|string[])} include - whitelist patterns to match.
   * @property {(string|string[])} exclude - blacklist patterns avoid matching.
   * @property {string} text - replace content with given text.
   * @property {string} file - replace with given file relative to project root.
   * @property {pathReplaceCallback} transform - path replace function.
   */

  /**
   * Import path replace pattern collection.
   * @type {Array<PathReplacePattern>}
   * @default []
   */
  replacePatterns: [
    {
      /**
       * Test path identifier string or regular expression.
       * @type {(string|RegExp)}
       * @default ''
       */
      test: './config/base-config',

      /**
       * Replace path string.
       * @type {string}
       * @default ''
       */
      replace: './config/replace-config'
    }
  ],

  /**
   * Bundle artifact build configuration.
   * @type {{}}
   */
  bundle: {

    /**
     * Bundle output external dependencies (dependency modules to treat as externals).
     * Refer rollup options for more info.
     * @type {Array<string>}
     * @default []
     */
    externals: [
      'regenerator-runtime/**',
      '@babel/runtime/**',
      '@babel/runtime-corejs2/**'
    ],

    /**
     * Bundle output global dependencies (dependency modules to tread as globals).
     * Refer rollup options for more info.
     * @type {{}}
     * @default {}
     */
    globals: {
      'react': 'React',
      'react-dom': 'ReactDOM'
    },

    /**
     * Treat globals as externals if true
     * @type {boolean}
     * @default true
     */
    mapExternals: true,

    /**
     * Browser compliant bundle modules formats (based on .babelrc bundle environment configuration)
     * - 'umd' – Universal Module Definition, works as amd, cjs and iife all in one
     * - 'amd' – Asynchronous Module Definition, used with module loaders like RequireJS
     * - 'iife' – A self-executing function, suitable for inclusion as a DOM script tag. (If you want to create a bundle
     * for your application, you probably want to use this, because it leads to smaller file sizes.)
     * - 'system' - Native format of SystemJS loader
     *
     * NodeJS only bundle module formats
     * 'cjs' – CommonJS, suitable for Node and Browserify/Webpack
     * 'esm' – Keep the bundle as an ES module file
     * @type {string}
     * @default 'umd'
     */
    format: 'umd',

    /**
     * Library global scope namespace (only applicable for browser compliant).
     * @type {string}
     * @default 'com.lib'
     */
    namespace: 'com.lib',

    /**
     * AMD flat bundle configuration
     * @type {{}}
     * @default {}
     */
    amd: {

      /**
       * AMD flat bundle define function name
       * @type {string}
       * @default ''
       */
      define: '',

      /**
       * AMD flat bundle module identifier name
       * @type {string}
       * @default 'my-lib'
       */
      id: 'my-lib'
    }
  },

  /**
   * Unit test configuration.
   * @type {{}}
   */
  test: {

    /**
     * Unit test framework
     *  - 'jasmine' - https://jasmine.github.io/
     *  - 'mocha' - https://mochajs.org/
     *  - 'jest' - https://jestjs.io/
     * @type {string}
     * @default 'jasmine'
     */
    framework: 'mocha',

    /**
     * Unit test environment.
     * - 'node' - nodejs only unit test environment to test none browser compliant libraries.
     * - 'browser' - browser based unit test environment with karma.
     * - 'jsdom' - browser like unit test environment in nodejs with jsdom.
     * - 'enzyme' - only supported when building react library with jest test framework.
     * @type {string}
     * @default 'node'
     */
    environment: 'node',

    /**
     * Unit test framework advanced options.
     * Caution! change only if you know what you are doing.
     * @type {{}}
     * @default {}
     */
    advanced: {

      /**
       * Jasmine CLI commands used with none browser test environments.
       * @type {{}}
       * @default {}
       */
      jasmine: {

        /**
         * Execute test spec on single run mode command.
         * @type {string}
         * @default 'jasmine --config=jasmine.json'
         */
        default: 'jasmine --config=jasmine.json',

        /**
         * Execute test spec on watch mode command.
         * Note: Jasmine does not support watch mode out of the box, hence chokidar is used to watch source changes.
         * @type {string}
         * @default 'jasmine --config=jasmine.json'
         */
        watch: 'jasmine --config=jasmine.json',

        /**
         * Execute test spec on single run mode with coverage support command.
         * @type {string}
         * @default 'nyc jasmine --config=jasmine.json'
         */
        coverageDefault: 'nyc jasmine --config=jasmine.json',

        /**
         * Execute test spec on watch mode with coverage support command.
         * Note: Jasmine does not support watch mode out of the box, hence chokidar is used to watch source changes.
         * @type {string}
         * @default 'nyc jasmine --config=jasmine.json'
         */
        coverageWatch: 'nyc jasmine --config=jasmine.json',
      },

      /**
       * Mocha CLI commands used with none browser test environments.
       * @type {{}}
       * @default {}
       */
      mocha: {

        /**
         * Execute test spec on single run mode command.
         * <ext-glob> is replaced with script extensions glob depending on script preprocessor at runtime.
         * @type {string}
         */
        default: 'mocha --opts mocha.opts "./{,!(node_modules)/**/}*.[sS]pec.<ext-glob>"',

        /**
         * Execute test spec on watch mode command.
         * <ext-glob> is replaced with script extensions glob depending on script preprocessor at runtime.
         * @type {string}
         */
        watch: 'mocha --opts mocha.opts --watch "./{,!(node_modules)/**/}*.[sS]pec.<ext-glob>"',

        /**
         * Execute test spec on single run mode with coverage support command.
         * <ext-glob> is replaced with script extensions glob depending on script preprocessor at runtime.
         * @type {string}
         */
        coverageDefault: 'nyc mocha --opts mocha.opts --watch "./{,!(node_modules)/**/}*.[sS]pec.<ext-glob>"',

        /**
         * Execute test spec on watch mode with coverage support command.
         * <ext-glob> is replaced with script extensions glob depending on script preprocessor at runtime.
         * @type {string}
         */
        coverageWatch: 'nyc mocha --opts mocha.opts --watch "./{,!(node_modules)/**/}*.[sS]pec.<ext-glob>"',
      },

      /**
       * Jest CLI commands used with all test environments.
       * @type {{}}
       * @default {}
       */
      jest: {

        /**
         * Execute test spec on single run mode command.
         * @type {string}
         * @default 'jest --config=jest.config.js'
         */
        default: 'jest --config=jest.config.js',

        /**
         * Execute test spec on watch mode command.
         * @type {string}
         * @default 'jest --config=jest.config.js --watch'
         */
        watch: 'jest --config=jest.config.js --watch',

        /**
         * Execute test spec on single run mode with coverage support command.
         * @type {string}
         * @default 'jest --config=jest.config.js --coverage'
         */
        coverageDefault: 'jest --config=jest.config.js --coverage',

        /**
         * Execute test spec on watch mode with coverage support command.
         * @type {string}
         * @default 'jest --config=jest.config.js --coverage --watch'
         */
        coverageWatch: 'jest --config=jest.config.js --coverage --watch',
      }
    }
  },

  /**
   * Watch mode serve configuration.
   * Set false if not required to serve on watch build.
   * @type {({}|false)}
   * @default {}
   */
  serve: {

    /**
     * Demo watch source directory which contains index.html to serve.
     * This path should be relative to root.
     * @type {string}
     * @default 'demo/watch'
     */
    demoDir: 'demo/watch',

    /**
     * Demo watch helper directory which contains helper scripts to serve.
     * This path should be relative to root.
     * @type {string}
     * @default 'demo/watch'
     */
    helperDir: 'demo/helper',

    /**
     * Additional serve directories.
     * These paths should be relative to root.
     * @type {Array<string>}
     * @default []
     */
    serveDir: [
      'node_modules/react/umd',
      'node_modules/react-dom/umd'
    ],

    /**
     * Open browser tab on watch mode build if true
     * @type {boolean}
     * @default true
     */
    open: true,

    /**
     * Watch source serve port.
     * @type {number}
     * @default 4000
     */
    port: 4000
  },

  /**
   * Bundle license configuration
   * @type {{}}
   * @default {}
   */
  license: {

    /**
     * Include inline header banner parsed via .packer/.banner.hbs template to build artifacts.
     * @type {boolean}
     * @default true
     */
    banner: true
  }

  /**
   * Code auto format configuration.
   * Auto format with https://prettier.io
   * @type {{}}
   * @default {}
   */
  format: {
    /**
     * File extensions to auto format.
     * @type {string[]}
     * @default [ 'js', 'jsx', 'ts', 'tsx', 'html', 'scss', 'css', 'less', 'json' ]
     */
    extensions: [ 'js', 'jsx', 'ts', 'tsx', 'html', 'scss', 'css', 'less', 'json' ],

    /**
     * Advance options to override formatter configuration.
     * Caution! change only if you know what you are doing.
     * @type {{}}
     */
    advanced: {

      /**
       * Prettier format command.
       * @type {string}
       */
      command: 'prettier --write **/*.{<ext-glob>}'
    }
  },

  /**
   * Linter configuration.
   * @type {{}}
   * @default {}
   */
  lint: {

    /**
     * Advance options to override linter configuration.
     * Caution! change only if you know what you are doing.
     * @type {{}}
     */
    advanced: {

      /**
       * Execute style lint command.
       * @type {string}
       */
      style: 'stylelint **/*.{styl,scss,sass,less,css}',

      /**
       * Execute tslint command.
       * @type {string}
       */
      typescript: 'tslint **/*.{ts,tsx}',

      /**
       * Execute eslint command.
       * @type {string}
       */
      javascript: 'eslint **/*.{js,mjs}'
    }
  }
};
```

## :seedling: Contributions

Feel free to open an issue or create a PR
