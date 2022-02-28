<h1 align="center">
  <br>&ensp;Svelte Color Picker
</h1>

<h4 align="center">
<a href="https://www.npmjs.com/package/svelte-material-color-picker"><img src="https://img.shields.io/npm/v/svelte-material-color-picker.svg"/></a>
<a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-blue.svg"/></a>
<!-- TODO POST IT ON MADE WITH SVELTE -->
<!-- <a href="https://madewithsvelte.com/p/svelte-tags-input/shield-link"><img src="https://madewithsvelte.com/storage/repo-shields/2151-shield.svg"/></a> -->
</h4>

<div class="hide-in-docs">

**[Live demo](https://kanban-demo.vercel.app/picker)**.

</div>

## Simple color picker made with Svelte
directly inspired from https://github.com/BennyAlex/material-design-inspired-color-picker 
<!-- TODO : ILLUTRATION IMG -->
<img src="https://raw.githubusercontent.com/V-Py/svelte-material-color-picker/master/static/colorpicker.png" alt="Svelte Kanban">

<slot />
## Installation

```sh
npm i svelte-material-color-picker
```

## Usage

```svelte
<script>
    import Picker from 'svelte-material-color-picker';
</script>


<Picker on:colorChanged {margin} {size} {colorsPerRow} {defaultTint} />

```

## Props
Full list of props/bindable variables for this component:

<div class="table">

<!-- prettier-ignore -->
| name             | default                                                    | description                                                                                                                                                                                    |
| :--------------- | :--------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `margin`        | 1 | Distance between color circles. |
| `size`   | 50  | Size of the colors circles.|
| `colorsPerRow`      | 6 | Number of color circles per row.|
| `defaultTint`  | 500 | Default tint displayed for each colors.|
| `selectedColor` | `#f44336` | The color selected, hex code with hashtag. |
| `mode` | `palette` | The mode of the color picker. `button` mode will hide after the palette after selecting a color only showing the color circle of the selected color. `palette` mode with show the palette and highlight the selected color in it. |
| `palette`      | <a href="">link palette</a> | The palette used by the picker.|

</div>

## Events
`Picker.svelte` dispatches the following event:

| name        | detail                                                                              | description                                                                                                                         |
| ----------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `colorChanged`       | `{ old:string, new:string }`                                                                | Triggers when clicking on a color picker.                                                                                           |

```svelte
<Kanban
  on:colorChanged={(e) => alert(`Color changed from ${e.detail.old} to ${e.detail.new}`)}
/>
```

## Dev Mode

```sh
git clone https://github.com/V-Py/svelte-material-color-picker
cd svelte-material-color-picker
npm install
npm run dev
```