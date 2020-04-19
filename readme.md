# Generate React CLI

[![dependencies](https://david-dm.org/arminbro/generate-react-cli.svg)](https://david-dm.org/arminbro/generate-react-cli)
[![License](https://img.shields.io/npm/l/express.svg)](https://github.com/arminbro/generate-react-cli/blob/master/LICENSE)

<p align="center"><img src="https://raw.githubusercontent.com/arminbro/generate-react-cli/master/docs/assets/component-cmd.gif?raw=true"/></p>

## Why?

To help speed up productivity in React projects and stop copying, pasting, and renaming files each time you want to create a new component.

**_A few notes:_**

- Now supports React [TypeScript](https://www.typescriptlang.org/) projects.
- Supports two different component testing libraries - [Testing Library](https://testing-library.com) and [Enzyme](https://airbnb.io/enzyme) - that work with [Jest](https://jestjs.io/). We assume that you have these libraries already configured in your React project.
- It follows [grouping by feature](https://reactjs.org/docs/faq-structure.html#grouping-by-file-type) because we believe when you look at a component, you should see all of its corresponding files (i.e., stylesheet, test, and component) under one folder with the component name. We feel this approach provides a better developer experience.

## You can install it globally and run it using npm:

```
 npm i -g generate-react-cli
 generate-react component Box
```

## Or you can just run it using npx like this:

```
 npx generate-react-cli component Box
```

_([npx](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b) is a package runner tool that comes with npm 5.2+ and higher)_

## Config File

When you run generate-react-cli within your project the first time, it will ask you a series of questions to customize the cli for your project needs (this will create a "generate-react-cli.json" config file).

### e.g. **generate-react-cli.json**

```json
{
  "usesTypeScript": false,
  "usesCssModule": true,
  "cssPreprocessor": "scss",
  "testLibrary": "Testing Library",
  "component": {
    "path": "src/components",
    "withStyle": true,
    "withTest": true,
    "withStory": true,
    "withLazy": false
  },
  "page": {
    "path": "src/pages",
    "withStyle": true,
    "withTest": true,
    "withStory": false,
    "withLazy": true
  }
}
```

## Usage

### Generate Component

```
 npx generate-react-cli component Box
```

This command will create a folder with your component name within your default (e.g. **src/components**) directory, and its corresponding files.

#### **Example of the component files structure**

```
|-- /src
    |-- /components
        |-- /Box
            |-- Box.js
            |-- Box.css
            |-- Box.test.js
```

#### Options

You can also override some of the generate-react-cli default component config options using one-off commands. So for example, let's say you have set **withTest** to be `true` in the component config property. You can override it like this:

```
 npx generate-react-cli component Box --withTest=false
```

Or vice versa, if you have set **withTest** to be `false` you can do this:

```
 npx generate-react-cli component Box --withTest=true
```

Otherwise, if you don't pass any options, it will just use the default values from the generate-react-cli config file you have set.

<table>
  <tr align="left">
    <th>Options</th>
    <th>Description</th>
    <th>Value Type</th>
  </tr>
  <tr>
    <td width="20%"><b>--path</b></td>
    <td width="60%">
      Value of the path where you want the component to be generated in (e.g. <b>src/pages</b>).  
    </td>
    <td width="20%">String</td>
  </tr>

  <tr>
    <td width="20%"><b>--withStyle</b></td>
    <td width="60%">
      Creates a corresponding stylesheet file with this component.    
    </td>
    <td width="20%">Boolean</td>
  </tr>

  <tr>
    <td width="20%"><b>--withTest</b></td>
    <td width="60%">
      Creates a corresponding test file with this component.      
    </td>
    <td width="20%">Boolean</td>
  </tr>

  <tr>
    <td width="20%"><b>--withStory</b></td>
    <td width="60%">
      Creates a corresponding story file with this component.      
    </td>
    <td width="20%">Boolean</td>
  </tr>

  <tr>
    <td width="20%"><b>--withLazy</b></td>
    <td width="60%">
      Creates a corresponding lazy file (a file that lazy-loads your component out of the box and enables <a href="https://reactjs.org/docs/code-splitting.html#code-splitting">code splitting</a>) with this component.      
    </td>
    <td width="20%">Boolean</td>
  </tr>
</table>

### Generate Page

```
 npx generate-react-cli page HomePage
```

This command will create a folder with your page name within your default (e.g. **src/pages**) directory, and its corresponding files.

#### **Example of the page files structure**

```
|-- /src
    |-- /pages
        |-- /HomePage
            |-- HomePage.js
            |-- HomePage.css
            |-- HomePage.test.js
```

#### Options

You can also override some of the generate-react-cli default page config options using one-off commands. So for example, let's say you have set **withTest** to be `true` in the page config property. You can override it like this:

```
 npx generate-react-cli page HomePage --withTest=false
```

Or vice versa, if you have set **withTest** to be `false` you can do this:

```
 npx generate-react-cli page HomePage --withTest=true
```

Otherwise, if you don't pass any options, it will just use the default values from the generate-react-cli config file you have set.

<table>
  <tr align="left">
    <th>Options</th>
    <th>Description</th>
    <th>Value Type</th>
  </tr>
  <tr>
    <td width="20%"><b>--path</b></td>
    <td width="60%">
      Value of the path where you want the page to be generated in (e.g. <b>src/pages</b>).  
    </td>
    <td width="20%">String</td>
  </tr>

  <tr>
    <td width="20%"><b>--withStyle</b></td>
    <td width="60%">
      Creates a corresponding stylesheet file with this page.    
    </td>
    <td width="20%">Boolean</td>
  </tr>

  <tr>
    <td width="20%"><b>--withTest</b></td>
    <td width="60%">
      Creates a corresponding test file with this page.      
    </td>
    <td width="20%">Boolean</td>
  </tr>

  <tr>
    <td width="20%"><b>--withStory</b></td>
    <td width="60%">
      Creates a corresponding story file with this page.      
    </td>
    <td width="20%">Boolean</td>
  </tr>

  <tr>
    <td width="20%"><b>--withLazy</b></td>
    <td width="60%">
      Creates a corresponding lazy file (a file that lazy-loads your page out of the box and enables <a href="https://reactjs.org/docs/code-splitting.html#code-splitting">code splitting</a>) with this page.      
    </td>
    <td width="20%">Boolean</td>
  </tr>
</table>

## License

Generate React CLI is open source software [licensed as MIT](https://github.com/arminbro/generate-react-cli/blob/master/LICENSE).
