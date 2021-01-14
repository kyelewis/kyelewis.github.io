---
title: "Vue and Typescript from scratch using Parcel bundler"
date: 2021-01-15T08:00:00+11:00
---

## Vue/Typescript with Parcel from scratch

For developers looking to get quickly on their feet with a reactive Vue app,
there are no shortage of templates, quick-starts and project generators 
for starting a new project.

**However... what if you want to create one from scratch?**

---
### Create the project folder
    # mkdir my-project          // MaKe DIRectory
    # cd my-project             // Change Directory

---

### Initialise package.json
Using -y skips the interactivity and uses all the defaults.

    # npm init -y
    Wrote to /Users/me/projects/my-project/package.json…

---

### Initialise an empty git repository
It won't be empty for long.

    # git init
    Initialized empty Git repository in /Users/me/projects/my-project/.git/

---

### Install the minimal required packages
_vue_ and _parcel-bundler_ are the core parts of this webapp.

_vue-class-components_ and _vue-property-decorators_ are used for decorator 
syntax when writing Vue apps. We could code without them just fine.

    # npm install parcel-bundler vue vue-class-components vue-property-decorator
    + vue-class-component@7.2.6
    + vue-property-decorator@9.1.2
    + vue@2.6.12
    + parcel-bundler@1.12.4
        added 747 packages from 469 contributors and audited 747 packages in 24.557s

---

### Create .gitignore
We want to make sure the _node_modules_ and _dist_ folders 
don't end up in version control.

    echo "node_modules\ndist" > .gitignore

---

### Make a git commit
Let's get this version control started.

    git add .
    git commit -m “Initialise package”

---

### Create basic directory structure
    mkdir src
    mkdir dist
    touch src/index.ts
    touch src/index.html
    touch src/App.vue

_Or for those who like to be efficient, **curly brackets expansions** are a neat shell trick!_

    mkdir {src,dist}
    touch {src/index.ts,src/index.html,src/App.vue}

---

### Make a git commit
Do it.

    git add .
    git commit -m “Create file structure”

---

### index.html
The only direct HTML file we'll write... 
a very basic page that includes the script
that will set up Vue
```
<html>
    <head>
        <title>My Project</title>
    </head>
    <body>
        <!-- ID matches the ID #app in index.ts -->
        <div id="app"></div>
    </body>
    <script src="./index.ts"></script>
</html>
```

### index.ts
Import the vue framework and our App component, and link them together.

    import Vue from "vue"               // Import the Vue framework
    import App from "./App.vue"         // Import your Vue Single File Component (SFC)

    // Create a new Vue instance using your App as the render function
    // and mount to the HTML element with the selector #app

    export default new Vue({render: h => h(App)})
        .$mount("#app")

### App.vue
This is the fun part. We're using Vue SFC (Single File Component) format here to write
a simple typescript Vue component.

```
<template>
    <div>{{ helloWorld }}</div>
</template>

<script lang="ts">

    import { Vue, Component } from "vue-property-decorator"

    @Component()
    export default class MyProjectApp extends Vue {
        helloWorld: string = "Hello, World!"
    }

</script>
```
### Make a git commit
    git add .
    git commit -m “Initial code commits”

### Add helpful scripts to package.json

Add these two to your package.json scripts section- use them to run your site
locally to test and to build the end package to upload to a host.

    "scripts": {
        "serve": "parcel serve src/index.html",
        "build": "parcel build src/index.html"
    },

_Or for command line heroes- do it with **jq** instead.._

    echo $(jq '.scripts.serve="parcel serve src/index.html" | .scripts.build="parcel build src/index.html"' package.json) | jq . > package.json

### Make a git commit
OK, maybe you don't have to make quite this many, but it's a good habit!

    git add .
    git commit -m “Set up package.json serve and build scripts”


### Serve and test!

    npm run serve

