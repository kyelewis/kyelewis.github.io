---
title: "Vue and Typescript from scratch using Parcel bundler"
date: 2021-01-14T21:00:00+11:00
---

## Vue/Typescript with Parcel from scratch

For developers looking to get quickly on their feet with a reactive Vue app,
there are no shortage of templates, quick-starts and project generators 
for starting a new project.

**However... what if you want to create one from scratch?**

---
### 1. Create the project folder
If you feel _my-project_ is a little underwhelming, choose a different name.

![Create the project folder](/static/vue-typescript-parcel-from-scratch/1.png)

---

### 2. Initialise package.json
Using -y skips the interactivity and uses all the defaults.

![npm init](/static/vue-typescript-parcel-from-scratch/2.png)

---
### 3. Initialise an empty git repository
It won't be empty for long.

![git init](/static/vue-typescript-parcel-from-scratch/3.png)

---
### 4. Install the minimal required packages
_vue_ and _parcel-bundler_ are the core parts of this webapp.

_vue-class-components_ and _vue-property-decorators_ are used for decorator 
syntax when writing Vue apps. We could code without them just fine.

![npm install](/static/vue-typescript-parcel-from-scratch/4.png)

---
### 5. Create .gitignore
We want to make sure the _node_modules_ and _dist_ folders 
don't end up in version control.

![.gitignore](/static/vue-typescript-parcel-from-scratch/5.png)

---
### 6. Make a git commit
Let's get this version control started.

![git add and commit](/static/vue-typescript-parcel-from-scratch/7.png)

---
### 7. Create basic directory structure
![Directory Structure - 1](/static/vue-typescript-parcel-from-scratch/8.png)

_Or for those who like to be efficient, **curly brackets expansions** are a neat shell trick!_

![Directory Structure - 2](/static/vue-typescript-parcel-from-scratch/8a.png)


---
### 8. Make a git commit
Might as well get used to it now.

![git push and commit - 2](/static/vue-typescript-parcel-from-scratch/9.png)


---
### 9. Writing index.html
The only direct HTML file we'll write, 
a very basic page that includes the script
that will set up Vue for us.

![index.html](/static/vue-typescript-parcel-from-scratch/10.png)

---
### 10. Writing index.ts
Import the vue framework and our App component, and link them together.

![index.ts](/static/vue-typescript-parcel-from-scratch/11.png)

---
### 11. Writing App.vue
This is the fun part. We're using Vue SFC (Single File Component) format here to write
a simple typescript Vue component.

![App.vue](/static/vue-typescript-parcel-from-scratch/12.png)

---
### 12. Make a git commit
![git add and commit](/static/vue-typescript-parcel-from-scratch/13.png)

---
### 13. Add helpful scripts to package.json

Add these two to your package.json scripts section- use them to run your site
locally to test and to build the end package to upload to a host.

![scripts](/static/vue-typescript-parcel-from-scratch/14.png)


_Or for command line heroes- do it with **jq** instead. Not really practical here, just interesting to show_

![jq](/static/vue-typescript-parcel-from-scratch/14a.png)

---
### 14. Make a git commit
OK, maybe you don't have to make quite this many, but it's a good habit!

![git add and commit](/static/vue-typescript-parcel-from-scratch/15.png)

---
### 15. Serve and test!

![npm run serve](/static/vue-typescript-parcel-from-scratch/16.png)
