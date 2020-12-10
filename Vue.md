---
date: '2019-01-12'
publish: 'true'
category: 'note'
author: 'Maitrik Patel'

title: 'Vue'
description: 'A progressive framework for building user interfaces'

topics: 'tools, development'

source: 'Github'
---

## Articles

- [React vs Vue](https://medium.com/javascript-in-plain-english/i-created-the-exact-same-app-in-react-and-vue-here-are-the-differences-2020-edition-36657f5aafdc)
- [React, Vue, and Svelte](https://medium.com/better-programming/react-vue-and-svelte-templates-side-by-side-4aa52cf3cf2)

## Tuts

- [VueJs Docs](https://vuejs.org/v2/guide/)
- [Vue Introduction - $](https://frontendmasters.com/courses/vue/)
- [Vue Advanced - $](https://frontendmasters.com/courses/advanced-vue/)
- [Vuex - $ ](https://frontendmasters.com/courses/vuex/)
- [Vue Mastery - $](https://www.vuemastery.com/)
- [Vue School - $](https://vueschool.io/)

## Examples

- [CodePen](https://codesandbox.io/s/linked-selects-th5w3?file=/src/App.vue:443-451)

---

## Vue Introduction [FEM]


### Resources

- [Vue Introduction Github](https://github.com/sdras/intro-to-vue)
- [Vue CodePen Collection](https://codepen.io/collection/noYZxW/?grid_type=list)

### Tools

- [Vue chrome devtools](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd?hl=en)
- [chrome extension](https://chrome.google.com/webstore/detail/codopen/agnkphdgffianchpipdbkeaclfbobaak)
- [vue vscode snippets](https://marketplace.visualstudio.com/items?itemName=sdras.vue-vscode-snippets)

## Challenges

- [Calculator using Directives](https://codepen.io/sdras/pen/vZjozM)


### Notes

#### Benefits

- clean
- semantic
- declarative
- legible
- easy to maintain
- reactive


#### Directives

**V-MODEL** - Creates a relationship between the data in the instance/component and a form input, so you can dynamically update values.

- `v-model.trim` will strip any leading or trailing whitespace from the bound string
- `v-model.number` changes strings to number inputs
- `v-model.lazy` won’t populate the content automatically, it will wait to bind until an event happens. (It listens to change events instead of input)

**V-IF / V-SHOW** - Is a conditional that will display information depending on meeting a requirement. This can be anything- buttons, forms, divs, components

- V-IF: mounting and remounting in DOM
- v-SHOW: toggling visibility by display:none

**V-IF / V-ELSE** - Pretty straightforward- you can conditionally render one thing or another. There's also v-else-if

**V-BIND or :** - One of the most useful directives so there's a shortcut! We can use it for so many things- class and style binding, creating dynamic props, etc...

**V-ONCE and V-PRE** - Not quite as useful, v-once will not update once it's been rendered. v-pre will print out the inner text exactly how it is, including code (good for documentation)

**V-HTML** - Great for strings that have html elements that need to be rendered!

- Not the same as templates: inserted as plain HTML.Don't use on user-rendered content, avoid XSS attacks

**V-TEXT** - Similar to using mustache templates

**V-ON or @** - Extremely useful so there's a shortcut! v-on is great for binding to events like click and mouseenter. You're able to pass in a parameter for the event like (e). We can also use ternaries directly

```JS
// <div @="
<div v-on="
  click   : onClick,
  keyup   : onKeyup,
  keydown : onKeydown
">
</div>
```

#### MODIFIERS

`@mousemove.stop` is comparable to e.stopPropagation()
`@mousemove.prevent` this is like e.preventDefault()
`@submit.prevent` this will no longer reload the page on submission
`@click.once` not to be confused with v-once, this click event will be triggered once.
`@click.native` so that you can listen to native events in the DOM