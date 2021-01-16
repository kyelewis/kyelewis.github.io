---
title: "Vue and Typescript from scratch using Parcel bundler"
date: 2021-01-14T21:00:00+11:00
---

## Vue/Typescript with Parcel from scratch

For developers looking to get quickly on their feet with a webapp,
there are no shortage of templates, quick-starts and project generators 
for starting a new project.

**However... what if you want to create one from scratch?**

It's not too hard to do!

---

# Prerequisites

### Node.JS
We need Node.JS to provide us with __npm__, the _Node Package Manager_.

Node.JS can be downloaded at [nodejs.org](https://nodejs.org/) - download 
and install the latest LTS version for your platform.

# Setting up our project

### Create the project folder
We need a folder to store our project in- we'll call ours _my-project_
```bash
$ mkdir my-project
$ cd my-project
````


### Create a package.json
NPM is the Node Package Manager, and it will help us install the required packages
need to make our app happen. 

__package.json__ is the file used by NPM to list information about your app, including what packages it depends on.

_npm_ includes a command to generate one of these for you, called __npm init__

Using the -y flag skips the interactivity and uses all the defaults- if you want, you can leave off -y
and answer the questions in the built-in questionaire.
```bash
$ npm init -y
Wrote to /Users/me/projects/my-project/package.json...
```


### Install the minimal required packages
For our web app, __Vue__ and __parcel-bundler__ are the core components.

__Vue__ is a framework to add _reactivity_ to web applications- it allows us to write
HTML just like a mail-merge email- with placeholders for data we can load or change live in code.

__Parcel__ is a program that takes our multiple files and helps link and bundle them
together into code that we can put directly on a web host.

_vue-class-components_ and _vue-property-decorators_ are used for extra 
syntax when writing Vue apps.

```bash
$ npm install parcel-bundler vue vue-class-components vue-property-decorator
 + vue-class-component@7.2.6
 + vue-property-decorator@9.1.2
 + vue@2.6.12
 + parcel-bundler@1.12.4
 added 747 packages from 469 contributors and audited 747 packages in 24.557s
```

### Create basic directory structure
```bash
$ mkdir src               # For all of our source code
$ mkdir dist              # The finished output we can upload to a host

# These three line are MacOS/Linux/WSL only... 
# On Windows, just create these three files in an editor
$ touch src/index.ts      # Typescript code
$ touch src/index.html    # HTML page
$ touch src/App.vue       # Vue app
```
_For linux, MacOS or WSL/WSL2 users who like to be efficient, **curly brackets expansions** are a neat shell trick!_
```bash
$ mkdir {src,dist}          # Expands to mkdir src; mkdir dist;
$ touch {src/index.ts,src/index.html,src/App.vue}
```

# Starting to write code

### Creating index.html
This is the only direct HTML file we'll write... 
a very basic page that includes the script
that will set up Vue.
```html
<html>

    <head>
        <title>My Project</title>
    </head>
    
    <body>
        <!-- ID matches the ID #app in index.ts, which we'll create next -->
        <div id="app"></div>
    </body>
    
    <!-- The script file that we're about to create next -->
    <script src="./index.ts"></script>

</html>
```

### Creating index.ts
This code imports the Vue framework and our App component, and links them together.
```javascript
import Vue from "vue"               // Import the Vue framework
import App from "./App.vue"         // Import your Vue Single File Component (SFC)

// Create a new Vue instance using your App as the render function
// and mount to the HTML element with the selector #app

export default new Vue({render: h => h(App)})
    .$mount("#app")
```
### App.vue
This is the fun part. We're using the Vue _SFC_ (Single File Component) format here to write
a simple typescript Vue component.

```vue
<template>
    <!-- Our HTML code including placeholder -->
    <div>{{ helloWorld }}</div>
</template>


<script lang="ts">
    import { Vue, Component } from "vue-property-decorator"

    @Component({})
    export default class MyProjectApp extends Vue {
      
        // Defining some text that we'll reference above.
        helloWorld: string = "Hello, World!"
      
    }
</script>
```

### Add some helpful scripts to package.json

The package.json has a section for including scripts that you can run and reference later.

Add these two to your package.json scripts section- the first __serve__ runs your website locally for your to test,
and the second __build__ creates a copy in dist/ for you to upload to a web host.
```json
{
  "scripts": {
    "serve": "parcel serve src/index.html",
    "build": "parcel build src/index.html"
  }
}
```


# Test your new webapp!

### Serve and test!
```bash
$ npm run serve

 > my-project@1.0.0 serve /Users/me/projects/my-project
 > parcel serve src/index.html

 Server running at http://localhost:1234
```

### Open your web browser
Visit http://localhost:1234 and enjoy the app!

What will you add next?

# More Resources
- Vue.js - [vuejs.org](https://vuejs.org/)
- Parcel - [parceljs.org](https://parceljs.org/)
- Typescript - [typescriptlang.org](https://typescriptlang.org/)
- Git - [git-scm.com](https://git-scm.com/)
- NPM - [npmjs.com](https://npmjs.com/)

