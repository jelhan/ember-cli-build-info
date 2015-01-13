# ember-cli-build-info

> Inject build info into your routes, controllers, and services.

*Note: this addon currently assumes you are using git for version control.*

Information includes:

```js
buildInfo: {
  version: '0.1.4', // pulled from package.json
  desc: 'v0.1.4-3-g53df212', // from shell command `git describe`
  commit: '53df212', // from `desc` above
}
```

In order to retrieve the git information, this addon runs a syncronous shell command using [exec-sync](https://www.npmjs.com/package/exec-sync).

## Installation

```bash
npm install --save-dev ember-cli-build-info
```

## Usage 

In a template:
```html
<p>Version: {{buildInfo.version}}</p>
<p>SHA: {{buildInfo.commit}}</p>
```

In a route, controller, or service:
```js
var buildInfo = this.buildInfo;
```

You can override the `buildInfo` key in your config file using the `ENV.buildInfoKey`.

```js
var ENV = {
  // ...
  buildInfoKey: 'appDeets', // now use `appDeets` instead of `buildInfo`
  // ...
}
```

## Options
Currently the only option is `metaTemplate` which allows you to inject a meta tag containing the build info.

`metaTemplate` is an opt-in option (defaults to `false`). Simply define a content template in your environment config:

```js
// ENV.APP.buildInfoOptions
buildInfoOptions: {
  metaTemplate: 'version:{VERSION}'
}
```

will result in:

```html
<meta name="build-info" content="version:0.0.2"/>
```

Available keys include `{VERSION}`, `{DESC}`, and `{COMMIT}`. These keys will be replaced by the current build info values.


# Collaborating

This README outlines the details of collaborating on this Ember addon.

* `git clone` this repository
* `npm install`
* `bower install`

## Running

* `ember server`
* Visit your app at http://localhost:4200.

## Running Tests

* `ember test`
* `ember test --server`

## Building

* `ember build`

For more information on using ember-cli, visit [http://www.ember-cli.com/](http://www.ember-cli.com/).
