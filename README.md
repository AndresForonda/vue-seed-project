### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

# Vue Seed project

The goal of this repository is to have a basic boilerplate for build Vue.js applications that scale,
the folder structure use it on it, allows to reduce context-shifting during the development.

Any suggestions or thoughts are welcome.

## Components folder

The components folder (src/components) serves as a source of components that can be reused through some
views.

These components can be grouped by functionality:

📦src  
 ┣ 📂components  
 ┃ ┣ 📂inputs  
 ┃ ┃ ┣ 📜TheDatePickerInput.vue  
 ┃ ┃ ┣ 📜TheRangeDateInput.vue  
 ┃ ┃ ┣ 📜TheSelectInput.vue  
 ┃ ┃ ┗ 📜TheTextInput.vue  
 ┃ ┗ 📂layout  
 ┃ ┃ ┣ 📜TheAppShell.vue  
 ┃ ┃ ┣ 📜TheBreadcrumb.vue  
 ┃ ┃ ┣ 📜TheHeader.vue  
 ┃ ┃ ┣ 📜TheNavBar.vue  
 ┃ ┃ ┗ 📜TheSideBar.vue  

### Composed components

Sometimes a component could be composed for more than one component, we can do a group like this:

📦src
 ┣ 📂components
 ┃ ┣ 📂inputs
 ┃ ┃ ┣ 📂the-drop-files-input
 ┃ ┃ ┃ ┣ 📂components
 ┃ ┃ ┃ ┃ ┣ 📜TheDropFilesArea.vue
 ┃ ┃ ┃ ┃ ┣ 📜TheDropFilesFooter.vue
 ┃ ┃ ┃ ┃ ┗ 📜TheDropFilesHeader.vue
 ┃ ┃ ┃ ┗ 📜TheDropFilesInput.vue

Above, the TheDropFilesInput.vue component is composed by the components TheDropFilesHeader.vue,
TheDropFilesArea.vue and TheDropFilesFooter.vue.

## Views

This folder is for store the application views, the proposed structure is intended to have
a similar hierarchy to each route in the application router.

To avoid context-shifting, the components that are not reusable through the application, and
belongs only to one specific view, should remain in the view or module folder.
.
src
+-- views/
+-- - home/
+-- - - HomeLayout.vue
+-- - - components/
+-- - - - HomeTitle.vue
+-- - - - HomeFooter.vue
+-- - - content/
+-- - - - HomeContentLayout.vue
+-- - - - components/
+-- - - - - HomeContentTable.vue
+-- - - - - HomeContentForm.vue
+-- - - - - HomeContentLoading.vue

📦src
 ┣ 📂components
 ┃ ┣ 📂buttons
 ┃ ┃ ┣ 📜TheButton.vue
 ┃ ┃ ┗ 📜TheCloseButton.vue
 ┃ ┣ 📂inputs
 ┃ ┃ ┣ 📂the-drop-files-input
 ┃ ┃ ┃ ┣ 📂components
 ┃ ┃ ┃ ┃ ┣ 📜TheDropFilesArea.vue
 ┃ ┃ ┃ ┃ ┣ 📜TheDropFilesFooter.vue
 ┃ ┃ ┃ ┃ ┗ 📜TheDropFilesHeader.vue
 ┃ ┃ ┃ ┗ 📜TheDropFilesInput.vue
 ┃ ┃ ┣ 📜TheDatePickerInput.vue
 ┃ ┃ ┣ 📜TheRangeDateInput.vue
 ┃ ┃ ┣ 📜TheSelectInput.vue
 ┃ ┃ ┗ 📜TheTextInput.vue
 ┃ ┗ 📂layout
 ┃ ┃ ┣ 📜TheAppShell.vue
 ┃ ┃ ┣ 📜TheBreadcrumb.vue
 ┃ ┃ ┣ 📜TheHeader.vue
 ┃ ┃ ┣ 📜TheNavBar.vue
 ┃ ┃ ┗ 📜TheSideBar.vue
 ┣ 📂router
 ┃ ┗ 📜index.js
 ┣ 📂store
 ┃ ┗ 📜index.js
 ┣ 📂views
 ┃ ┣ 📜About.vue
 ┃ ┗ 📜Home.vue
 ┣ 📜App.vue
 ┗ 📜main.js



# seed-project-6connex

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Run your unit tests

```
npm run test:unit
```

### Run your end-to-end tests

```
npm run test:e2e
```

### Lints and fixes files

```
npm run lint
```