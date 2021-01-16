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


### Start an empty git repository
We'll use the widely popular _git_ version control system, 
for keeping track of our code changes.
```bash
$ git init
Initialized empty Git repository in /Users/me/projects/my-project/.git/
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

### Create .gitignore
Typically, we only want to keep source code and resources like images in our source control-
we can create a .gitignore file to tell git which files not to include.

We have two folders of interest here so far- _node_modules_ contains local package files that npm
downloads, and _dist_ is the output of our web page. Neither of these are our own source code.

Either create a file named .gitignore with the following contents:
```
node_modules
dist
```

or use this quick bash command to achieve the same result:

```bash
$ echo "node_modules\ndist" > .gitignore
```


### Make your first git commit
Let's get this version control started.
```bash
$ git add .                           # Add all files. 
$ git commit -m "Initialise package"  # Snapshot these in to a new commit with a message
```

### Create basic directory structure
```bash
$ mkdir src               # For all of our source code
$ mkdir dist              # The finished output we can upload to a host
$ touch src/index.ts      # Typescript code
$ touch src/index.html    # HTML page
$ touch src/App.vue       # Vue app
```
_Or for those who like to be efficient, **curly brackets expansions** are a neat shell trick!_
```bash
$ mkdir {src,dist}          # Expands to mkdir src; mkdir dist;
$ touch {src/index.ts,src/index.html,src/App.vue}
```

### Make another git commit
Keep it up, it's a good habit to commit regularly, so you have more useful commits to use
in the future, if you need to roll back. Always include a useful message.
```bash
$ git add .
$ git commit -m "Create file and folder structure"
```
---

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

```Vue
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
### Make a git commit
```bash
$ git add .
$ git commit -m "Initial code"
```

### Add some helpful scripts to package.json

The package.json has a section for including scripts that you can run and reference later.

Add these two to your package.json scripts section- the first __serve__ runs your website locally for your to test,
and the second __build__ creates a copy in dist/ for you to upload to a web host.
```json
"scripts": {
  "serve": "parcel serve src/index.html",
  "build": "parcel build src/index.html"
},
```
### Make a git commit
OK, maybe you don't have to make quite this many, but it's a good habit to start.
```bash
$ git add .
$ git commit -m "Set up package.json serve and build scripts"
```

---
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

# Follow-up Resources
- Vue.js - https://vuejs.org/
- Parcel - https://parceljs.org/
- Typescript - https://www.typescriptlang.org/
- Git - https://git-scm.com/
- NPM - https://www.npmjs.com/

