# How to install
If you would like to install the Power BI visuals ChartUtils to your custom visual please pay attention to these items:
* [Requirements](#requirements)
* [Installation](#installation)
* [Including declarations to the build flow](#including-declarations-to-the-build-flow)
* [Including JavaScript artifacts to the custom visual](#including-javascript-artifacts-to-the-custom-visual)
* [Including CSS artifacts to the custom visual](#including-css-artifacts-to-the-custom-visual)

## Requirements
To use the package you should have the following things:
* [node.js](https://nodejs.org) (we recommend the latest LTS version)
* [npm](https://www.npmjs.com/) (the minimal supported version is 3.0.0)
* The custom visual created by [PowerBI-visuals-tools](https://github.com/Microsoft/PowerBI-visuals-tools)

## Installation
To install the package you should run the following command in the directory with your current custom visual:

```bash
npm install powerbi-visuals-utils-chartutils --save
```

This command installs the package and adds a package as a dependency to your ```package.json```

After installation of the package, you should install the [typings](https://www.npmjs.com/package/typings) package as a global dependency by using the following command:
```bash
npm install typings -g
```

After that, you should run the following command in the directory with your current custom visual:
```bash
typings install --save --global dt~d3#0.0.0+20160907005744 dt~jquery#1.10.0+20160929162922 dt~lodash#4.14.0+20161110215204
```

This command installs type declarations to the ```typings``` directory. These declarations are necessary for TypeScript compiler and Intellisense.

## Including declarations to the build flow
The package contains ```d.ts``` declarations file, it's necessary for TypeScript compiler and it helps to develop your visuals fast and confident. You should add the following files to the ```files``` property of ```tsconfig.json```:
* ```typings/index.d.ts```
* ```node_modules/powerbi-visuals-utils-formattingutils/lib/index.d.ts```
* ```node_modules/powerbi-visuals-utils-interactivityutils/lib/index.d.ts```
* ```node_modules/powerbi-visuals-utils-svgutils/lib/index.d.ts```
* ```node_modules/powerbi-visuals-utils-typeutils/lib/index.d.ts```
* ```node_modules/powerbi-visuals-utils-chartutils/lib/index.d.ts```

As a result you will have the following file structure:
```json
{
  "compilerOptions": {...},
  "files": [
    "typings/index.d.ts",
    "node_modules/powerbi-visuals-utils-formattingutils/lib/index.d.ts",
    "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.d.ts",
    "node_modules/powerbi-visuals-utils-svgutils/lib/index.d.ts",
    "node_modules/powerbi-visuals-utils-typeutils/lib/index.d.ts",
    "node_modules/powerbi-visuals-utils-chartutils/lib/index.d.ts"
  ]
}
```

## Including JavaScript artifacts to the custom visual
To use the package with your custom visuals you should add the following files to the ```externalJS``` property of ```pbiviz.json``` :
* ```node_modules/jquery/dist/jquery.min.js```
* ```node_modules/d3/d3.min.js```
* ```node_modules/lodash/lodash.min.js```
* ```node_modules/globalize/lib/globalize.js```
* ```node_modules/globalize/lib/cultures/globalize.culture.en-US.js```
* ```node_modules/powerbi-visuals-utils-typeutils/lib/index.js```
* ```node_modules/powerbi-visuals-utils-svgutils/lib/index.js```
* ```node_modules/powerbi-visuals-utils-formattingutils/lib/index.js```
* ```node_modules/powerbi-visuals-utils-interactivityutils/lib/index.js```
* ```node_modules/powerbi-visuals-utils-chartutils/lib/index.js```

As a result you will have the following file structure:
```json
{
  "visual": {...},
  "apiVersion": ...,
  "author": {...},
  "assets": {...},
  "externalJS": [
    "node_modules/jquery/dist/jquery.min.js",
    "node_modules/d3/d3.min.js",
    "node_modules/lodash/lodash.min.js",
    "node_modules/globalize/lib/globalize.js",
    "node_modules/globalize/lib/cultures/globalize.culture.en-US.js",
    "node_modules/powerbi-visuals-utils-typeutils/lib/index.js",
    "node_modules/powerbi-visuals-utils-svgutils/lib/index.js",
    "node_modules/powerbi-visuals-utils-formattingutils/lib/index.js",
    "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.js",
    "node_modules/powerbi-visuals-utils-chartutils/lib/index.js"
  ],
  "style": ...,
  "capabilities": ...
}
```

## Including CSS artifacts to the custom visual
To use the package with your custom visuals you should import the following CSS files to your ```.less``` file:

* ```node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css```
* ```node_modules/powerbi-visuals-utils-chartutils/lib/index.css```

As a result you will have the following file structure:
```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
@import (less) "node_modules/powerbi-visuals-utils-chartutils/lib/index.css";
```

Please note, you should import ```.css``` files as ```.less``` files, because Power BI Visuals Tools wraps the external CSS rules.

That's it. :rocket: :metal: That's a good time to read our [Usage Guide](./usage-guide.md).
