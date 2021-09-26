Yarn 3 doesn't seem to recognise this packageExtension on `graphql.macro`.

Despite this declaration in `.yarnrc.yml`:

```yml
packageExtensions: //Same versions as in package.json
  "graphql.macro@^1.4.2":
    dependencies:
      \@babel/runtime: ^7.15.4
```

`yarn build` still yields this result:

```
[thomas@thomas-mbp ~/code/web/dep_repro] master yarn build
Creating an optimized production build...
Browserslist: caniuse-lite is outdated. Please run:
npx browserslist@latest --update-db

Why you should do it regularly:
https://github.com/browserslist/browserslist#browsers-data-updating
Failed to compile.

./src/App.tsx
Error: /Users/thomas/code/web/dep_repro/src/App.tsx: graphql.macro tried to access @babel/runtime, but it isn't declared in its dependencies; this makes the require call ambiguous and unsound.

Required package: @babel/runtime (via "@babel/runtime/helpers/interopRequireDefault")
Required by: graphql.macro@npm:1.4.2 (via /Users/thomas/code/web/dep_repro/.yarn/cache/graphql.macro-npm-1.4.2-ddfe75167b-a9cf5e3c1a.zip/node_modules/graphql.macro/lib/)

Require stack:
- /Users/thomas/code/web/dep_repro/.yarn/cache/graphql.macro-npm-1.4.2-ddfe75167b-a9cf5e3c1a.zip/node_modules/graphql.macro/lib/index.js
- /Users/thomas/code/web/dep_repro/.yarn/cache/babel-plugin-macros-npm-2.8.0-451367d7e7-59b09a21cf.zip/node_modules/babel-plugin-macros/dist/index.js
- /Users/thomas/code/web/dep_repro/.yarn/cache/babel-preset-react-app-npm-10.0.0-ee0b2d04e6-d117a1384b.zip/node_modules/babel-preset-react-app/create.js
- /Users/thomas/code/web/dep_repro/.yarn/cache/babel-preset-react-app-npm-10.0.0-ee0b2d04e6-d117a1384b.zip/node_modules/babel-preset-react-app/index.js
- /Users/thomas/code/web/dep_repro/.yarn/cache/@babel-core-npm-7.12.3-209b619ca0-29ee14dd7a.zip/node_modules/@babel/core/lib/config/files/plugins.js
- /Users/thomas/code/web/dep_repro/.yarn/cache/@babel-core-npm-7.12.3-209b619ca0-29ee14dd7a.zip/node_modules/@babel/core/lib/config/files/index.js
- /Users/thomas/code/web/dep_repro/.yarn/cache/@babel-core-npm-7.12.3-209b619ca0-29ee14dd7a.zip/node_modules/@babel/core/lib/index.js
- /Users/thomas/code/web/dep_repro/.yarn/__virtual__/babel-loader-virtual-8767f37185/0/cache/babel-loader-npm-8.1.0-e8c38740ba-fdbcae91cc.zip/node_modules/babel-loader/lib/index.js
- /Users/thomas/code/web/dep_repro/.yarn/cache/loader-runner-npm-2.4.0-c414104c2f-e27eebbca5.zip/node_modules/loader-runner/lib/loadLoader.js
- /Users/thomas/code/web/dep_repro/.yarn/cache/loader-runner-npm-2.4.0-c414104c2f-e27eebbca5.zip/node_modules/loader-runner/lib/LoaderRunner.js
- /Users/thomas/code/web/dep_repro/.yarn/__virtual__/webpack-virtual-0912c7b7ea/0/cache/webpack-npm-4.44.2-eedc4b763e-3d42ee6af7.zip/node_modules/webpack/lib/NormalModule.js
- /Users/thomas/code/web/dep_repro/.yarn/__virtual__/webpack-virtual-0912c7b7ea/0/cache/webpack-npm-4.44.2-eedc4b763e-3d42ee6af7.zip/node_modules/webpack/lib/NormalModuleFactory.js
- /Users/thomas/code/web/dep_repro/.yarn/__virtual__/webpack-virtual-0912c7b7ea/0/cache/webpack-npm-4.44.2-eedc4b763e-3d42ee6af7.zip/node_modules/webpack/lib/Compiler.js
- /Users/thomas/code/web/dep_repro/.yarn/__virtual__/webpack-virtual-0912c7b7ea/0/cache/webpack-npm-4.44.2-eedc4b763e-3d42ee6af7.zip/node_modules/webpack/lib/webpack.js
- /Users/thomas/code/web/dep_repro/.yarn/__virtual__/react-scripts-virtual-77199ba4db/0/cache/react-scripts-npm-4.0.3-119b1229eb-a05a46ce31.zip/node_modules/react-scripts/scripts/build.js


[thomas@thomas-mbp ~/code/web/dep_repro] master
```
