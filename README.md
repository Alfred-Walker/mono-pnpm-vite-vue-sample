# **Project Reproduction Procedure (TS)**
  
### 0. create & enter directory

### 1. Initialize pnpm
  
```pnpm init```

### 2. Add Typescript definitions for node
  
```pnpm add -D typescript @types/node```

### 3. Make pnpm-workspace.yaml with subprojects to develop
  
```
packages:
  - "project-0"
  - "project-1"
  - "project-2"
```
  
### 4. Make subprojects (See https://vitejs.dev/guide/ for templates)
  
```
pnpm create vite project-0 --template vue-ts
pnpm create vite project-1 --template vue-ts
pnpm create vite project-2 --template vue-ts
...
```

### 5. Change name and add dependencies for other subprojects

```
e.g. package.json (project-0)
{
    "name": "@mono-pnpm-vite-vue-sample/project-0",
    ...
    "dependencies": {
        "@mono-pnpm-vite-vue-sample/project-1": "workspace:*",
        "@mono-pnpm-vite-vue-sample/project-2": "workspace:*",
        ...
    }
}
```

### 6. Install packages for subprojects
  
```pnpm install (per each subproject)```


### 7. Run!
  
```pnpm run dev (to launch)```



### (Bonus) Fix "scripts" in package.json in root directory to prevent dvelopers from executing npm install.

  ```
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "preinstall": "npx only-allow pnpm"
  },

  ```
(See also project-0/src/App.vue referencing "helloProject" of project-1 and project-2.)
