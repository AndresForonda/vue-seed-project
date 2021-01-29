# Vue Seed project

The goal of this repository is to have a basic boilerplate for build Vue.js applications that scale,
the folder structure use it on it, allows to reduce context-shifting during the development.

Any suggestions or thoughts are welcome.

## Libraries

A list of mandatory/suggested libraries for specific development purposes (i.e. UI, date format, download files, etc.).

### Mandatory libraries

- UI: [BootstrapVue](https://bootstrap-vue.org/) ⛩
- CSS: [Tailwind CSS](https://tailwindcss.com/docs) 🏳️‍🌈
- HTTP Client: [Axios](https://github.com/axios/axios) 💻

### Suggested libraries
### Suggestions

- Date format: native Date (TODO: implement date format tool)


## Components folder

The components folder (src/components) serves as a source of components that can be reused through some
views.

These components can be grouped by functionality:
```
📦src
 ┣ 📂components
 ┃ ┣ 📂buttons
 ┃ ┃ ┣ 📜VButton.vue
 ┃ ┃ ┗ 📜VButtonClose.vue
 ┃ ┣ 📂inputs
 ┃ ┃ ┣ 📜VDatePickerInput.vue
 ┃ ┃ ┣ 📜VRangeDateInput.vue
 ┃ ┃ ┣ 📜VSelectInput.vue
 ┃ ┃ ┗ 📜VTextInput.vue
 ┃ ┗ 📂layout
 ┃ ┃ ┣ 📜TheAppShell.vue
 ┃ ┃ ┣ 📜TheBreadcrumb.vue
 ┃ ┃ ┣ 📜TheHeader.vue
 ┃ ┃ ┣ 📜TheNavBar.vue
 ┃ ┃ ┗ 📜TheSideBar.vue
```

### Composed components

Sometimes a component could be composed for more than one component, we can do a group like this:
```
📦src
 ┣ 📂components
 ┃ ┣ 📂inputs
 ┃ ┃ ┣ 📂v-drop-files-input
 ┃ ┃ ┃ ┣ 📂components
 ┃ ┃ ┃ ┃ ┣ 📜VDropFilesArea.vue
 ┃ ┃ ┃ ┃ ┣ 📜VDropFilesFooter.vue
 ┃ ┃ ┃ ┃ ┗ 📜VDropFilesHeader.vue
 ┃ ┃ ┃ ┗ 📜VDropFilesInput.vue
 ```

The TheDropFilesInput.vue component is composed by the components TheDropFilesHeader.vue,
TheDropFilesArea.vue and TheDropFilesFooter.vue.


## Views

This folder is for store the application views, the proposed structure is intended to have
a similar hierarchy to each route in the application router.


### Basic structure

To avoid context-shifting, the components that are not reusable through the application, and
belongs only to one specific view, should remain in the view or module folder.

```
📦src
 ┣ 📂views
 ┃ ┣ 📂about
 ┃ ┃ ┣ 📂components
 ┃ ┃ ┃ ┗ 📜AboutList.vue
 ┃ ┃ ┣ 📂content
 ┃ ┃ ┃ ┗ 📜AboutContentLayout.vue
 ┃ ┃ ┗ 📜AboutLayout.vue
```

- The AboutLayout.vue component serves as entry point of the view for the router.
- The components folder stores basic components used in the AboutLayout.vue, it could be filters used to change the content, buttons to redirect to another views, or information legends of the view, but they are not part of the main purpose of the view.
- The AboutContentLayout.vue is the component used to show the main content of the view (i.e. a tables, graphics, forms).
- This pattern is flexible, if there are not required components or a complex content, so the view is quite simple, just use the AboutLayout.vue component. (i.e. 404, error, loading).


### Default views

The default views are a kind of single purpose views, they help to show information about the state of the application.

```
📦src
 ┣ 📂views
 ┃ ┣ 📂default-views
 ┃ ┃ ┣ 📜404.vue
 ┃ ┃ ┣ 📜ViewError.vue
 ┃ ┃ ┗ 📜ViewLoading.vue
```

- 404.vue view could be used when there is a wrong route.
- ViewError.vue view could be used when there are some errors while loading the view, having a way to give feedback to the user (something went wrong).
- ViewLoading.vue view could be used while the actual route still loading the components of the view.


### Content folder

The content of the view could be complex, maybe can be composed for many components, so having a content folder with its own layout file and components folder is a good way to organize it.

```
📦src
 ┣ 📂views
 ┃ ┣ 📂home
 ┃ ┃ ┗ 📜HomeLayout.vue
 ┃ ┃ ┣ 📂components
 ┃ ┃ ┃ ┗ 📜HomeHeader.vue
 ┃ ┃ ┣ 📂content
 ┃ ┃ ┃ ┗ 📜HomeContentLayout.vue
 ┃ ┃ ┃ ┣ 📂components
 ┃ ┃ ┃ ┃ ┗ 📜HomeContentTable.vue
 ┃ ┃ ┃ ┃ ┣ 📂home-content-options
 ┃ ┃ ┃ ┃ ┃ ┗ 📜HomeContentOptions.vue
 ┃ ┃ ┃ ┃ ┃ ┣ 📂components
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜HomeContentOptionsList.vue
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜HomeContentOptionsModal.vue
```


- The HomeLayout.vue component is composed by the HomeHeader.vue component and the HomeContentLayout.vue.
- The HomeContentLayout.vue component is composed by two components, the HomeContentTable and HomeContentOptions.vue.
- The HomeContentOptions.vue component is composed by two components, the HomeContentOptionsList.vue and HomeContentOptionsModal.vue

Yeah, it could be overwhelming, it's nested, very nested, I mean, it's really nested!, but going further, the context of each component and its components is clear and coupled.

#### Comparing structures

- Proposed vs Single root, folder structures

- - Proposed

```
📦src
 ┣ 📂views
 ┃ ┣ 📂home
 ┃ ┃ ┣ 📂components
 ┃ ┃ ┣ 📂content
 ┃ ┃ ┃ ┣ 📂components
 ┃ ┃ ┃ ┃ ┣ 📂home-content-options
 ┃ ┃ ┃ ┃ ┃ ┣ 📂components
```


- - Single root

```
📦src
 ┣ 📂views
 ┃ ┣ 📂home
```

- Proposed vs Single root, file structure

- - Proposed

```
📦src
 ┣ 📂views
 ┃ ┣ 📂home
 ┃ ┃ ┣ 📜HomeLayout.vue
 ┃ ┃ ┣ 📂components
 ┃ ┃ ┃ ┣ 📜HomeHeader.vue
 ┃ ┃ ┃ ┣ 📜HomeFooter.vue
 ┃ ┃ ┃ ┣ 📜HomeOptions.vue
 ┃ ┃ ┃ ┗ 📜HomeSideNotes.vue
 ┃ ┃ ┣ 📂content
 ┃ ┃ ┃ ┣ 📜HomeContentLayout.vue
 ┃ ┃ ┃ ┣ 📂components
 ┃ ┃ ┃ ┃ ┣ 📜HomeContentTable.vue
 ┃ ┃ ┃ ┃ ┣ 📜HomeContentTools.vue
 ┃ ┃ ┃ ┃ ┣ 📂home-content-options
 ┃ ┃ ┃ ┃ ┃ ┣ 📜HomeContentOptions.vue
 ┃ ┃ ┃ ┃ ┃ ┣ 📂components
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜HomeContentOptionsList.vue
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜HomeContentOptionsModal.vue
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜HomeContentOptionsLoad.vue
```

- - Single root

```
📦src
 ┣ 📂views
 ┃ ┣ 📂home 
 ┃ ┃ ┣ 📜HomeContentOptions.vue
 ┃ ┃ ┣ 📜HomeContentOptionsList.vue
 ┃ ┃ ┣ 📜HomeContentOptionsModal.vue
 ┃ ┃ ┣ 📜HomeContentOptionsLoad.vue
 ┃ ┃ ┣ 📜HomeContentLayout.vue
 ┃ ┃ ┣ 📜HomeContentTable.vue 
 ┃ ┃ ┣ 📜HomeContentTools.vue
 ┃ ┃ ┣ 📜HomeFooter.vue
 ┃ ┃ ┣ 📜HomeHeader.vue
 ┃ ┃ ┣ 📜HomeLayout.vue
 ┃ ┃ ┣ 📜HomeOptions.vue
 ┃ ┃ ┣ 📜HomeSideNotes.vue
```

- Proposed vs Single root, working context (HomeContentOptions)

- - Proposed

```
📂home-content-options
 ┣ 📜HomeContentOptions.vue
 ┣ 📂components
 ┃ ┣ 📜HomeContentOptionsList.vue
 ┃ ┣ 📜HomeContentOptionsModal.vue
 ┃ ┗ 📜HomeContentOptionsLoad.vue
```

- - Single root

```
 📂home 
 ┣ 📜HomeContentOptions.vue
 ┣ 📜HomeContentOptionsList.vue
 ┣ 📜HomeContentOptionsModal.vue
 ┣ 📜HomeContentOptionsLoad.vue
 ┣ 📜HomeContentLayout.vue
 ┣ 📜HomeContentTable.vue 
 ┣ 📜HomeContentTools.vue
 ┣ 📜HomeFooter.vue
 ┣ 📜HomeHeader.vue
 ┣ 📜HomeLayout.vue
 ┣ 📜HomeOptions.vue
 ┣ 📜HomeSideNotes.vue
```


# seed-project-6connex

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

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
# tw-vue-bootstrap-template
Template for VUE.js projects
