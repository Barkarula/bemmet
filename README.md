# bemmet

Simple Emmet-like tool to expand abbreviations into [BEMJSON](https://en.bem.info/technology/bemjson/).
Check out [online demo](http://tadatuta.github.io/bemmet/).

Also available as [Sublime Text](https://github.com/tadatuta/sublime-bemmet) and [Atom](https://atom.io/packages/atom-bemmet) plugins.

## Usage
```js
var bemmet = require('bemmet');
var bemjson = bemmet('b1>__e1*2>b3_theme_islands+_state_active{hello}'); // object
var bemjsonString = bemmet.stringify('b1>__e1*2>b3_theme_islands+_state_active{hello}');

console.log(bemjsonString);
// {
//     block: 'b1',
//     content: [
//         {
//             block: 'b1',
//             elem: 'e1',
//             content: [
//                 {
//                     block: 'b3',
//                     mods: { theme: 'islands' },
//                     content: {}
//                 },
//                 {
//                     block: 'b1',
//                     mods: { state: 'active' },
//                     content: 'hello'
//                 }
//             ]
//         },
//         {
//             block: 'b1',
//             elem: 'e1',
//             content: [
//                 {
//                     block: 'b3',
//                     mods: { theme: 'islands' },
//                     content: {}
//                 },
//                 {
//                     block: 'b1',
//                     mods: { state: 'active' },
//                     content: 'hello'
//                 }
//             ]
//         }
//     ]
// }
```

### Custom naming scheme
```js
var bemmet = require('bemmet');
var abbreviation = 'b1>__e1*2>b3--islands+--active';
var bemjson = bemmet.stringify(abbreviation, {
    naming: {
        elem: '__',
        mod: '--'
    }
});

console.log(bemjson);
// {
//     block: 'b1',
//     content: [
//         {
//             block: 'b1',
//             elem: 'e1',
//             content: [
//                 {
//                     block: 'b3',
//                     mods: { islands: true },
//                     content: {}
//                 },
//                 {
//                     block: 'b1',
//                     mods: { active: true },
//                     content: {}
//                 }
//             ]
//         },
//         {
//             block: 'b1',
//             elem: 'e1',
//             content: [
//                 {
//                     block: 'b3',
//                     mods: { islands: true },
//                     content: {}
//                 },
//                 {
//                     block: 'b1',
//                     mods: { active: true },
//                     content: {}
//                 }
//             ]
//         }
//     ]
// }
```
