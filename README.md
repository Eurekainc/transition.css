<p align="center">
  <img src="https://img.shields.io/npm/dt/transition.css.svg" alt="Total Downloads">
  <img src="https://img.shields.io/npm/v/transition.css.svg" alt="Latest Release">
  <img src="https://img.shields.io/npm/l/transition.css.svg" alt="License">
  <img src="https://api.netlify.com/api/v1/badges/58d0ecf5-6241-4209-aa35-cf09983e0b37/deploy-status" alt="Netlify Status">
</p>

<p align="center">
<a href="https://transition.style" target="_blank">
<img src="https://github.com/argyleink/transition.css/blob/main/demo/kitchen-sink.gif?raw=true" />
</a>
</p>

<br>

## Basics
<img src="https://github.com/argyleink/transition.css/blob/main/demo/wipe-up.gif?raw=true" />

```html
<link rel="stylesheet" href="https://unpkg.com/transition-style">

<div transition="in:wipe:up">
  👍
</div>
```

Choose from **46 pre-built transitions!**  

Hands on at [Codepen](https://codepen.io/argyleink/pen/RwrzGJb) or preview all 46 @ [transition.style](https://transition.style)

<br>

## Installation
#### NPM  
1. `npm i transition-style` 
2. import from **CSS**
```css
@import "transition-style";
```
3. or import from **JS** 
```js
import 'transition-style';
```

<br>

#### CDN 
`https://unpkg.com/transition-style`  

**Individual Category Bundles**
  - **Circles** `https://unpkg.com/transition-style/transition.circles.min.css`
  - **Squares** `https://unpkg.com/transition-style/transition.squares.min.css`
  - **Polygons** `https://unpkg.com/transition-style/transition.polygons.min.css`
  - **Wipes** `https://unpkg.com/transition-style/transition.wipes.min.css`

<br>

### 👉 The Hackpack 
`https://unpkg.com/transition-style/transition.hackpack.min.css`  

**More options, more control, smaller import**  
by importing only the custom properties and base styles:
- compose custom transition combinations
- create multi-part transitions
- use classes or CSS-in-JS that leverage transition.css custom props

> Custom properties ship with each `.min.css` as well
  
<br>
<img src="https://github.com/argyleink/transition.css/blob/main/demo/opposing-corner-fold.gif?raw=true" />
<br><br>

## Usage
After `transition.css` has been added to your project, add an attribute to an element and watch the magic:  

```html
<div transition="in:circle:bottom-right">
  A transitioned IN element
</div>

<div transition="out:wipe:down">
  A transitioned OUT element
</div>
```

> if nothing is happening when using the attributes, it's likely `transition.css` has not loaded

#### Using `@keyframes`
Each bundle ships with the `@keyframes` declared, and you can use them as you see fit. You can use these to build your own animations or just hook into the presets in your own way:

```css
.main--state-in {
  animation: wipe-in-left; /* https://github.com/argyleink/transition.css/blob/main/src/wipes/in-left.css */
  animation-duration: 2s;
  animation-fill-mode: both;
}
```

#### Using CSS Custom Properties
Each bundle ships with clearly named custom properties which contain the state and geometry needed to orchestrate custom transitions. 

```css
.overrides {
  --transition__duration: 1s;            /* default: 2.5s */
  --transition__easing: ease-in-out;     /* default: cubic-bezier(.25, 1, .30, 1) */
  --transition__delay: 1s;               /* default: 0 */
}
```

or target a specific transition and override it's defaults:

```css
[transition="in:wipe:up"] {
  --transition__duration: 1s;
}
```

Go off the rails and build your own transitions with these variables. There's even the `hackpack` which is exclusively the custom props 🤘💀 Most of the built in transitions are from the center in Transition.css, here's how you can set the `from` transition to somewhere custom:

```css
@keyframes circle-swoop {
  from {
    clip-path: var(--circle-top-right-out);
  }
  to {
    clip-path: var(--circle-bottom-right-in);
  }
}

.--in-custom {
  --transition__duration: 1s;
  --transition__easing: ease-in-out;
  animation-name: circle-swoop;
}
```

Then, in the HTML:

```html
<div transition class="... --in-custom">
  A custom transitioned element
</div>
```

> The only rule is that you must transition from the same type of shapes

At this point you're using Transition.css to it's maximum. You can reach a huge set of transitions by using the custom properties. Have fun!

#### Play
Play and experiment with [this Codepen](https://codepen.io/argyleink/pen/RwrzGJb)

<br><br>

## Development
See the `svelte` branch.

## Production
`npm run bundle` concurrently bundles and minifies. 
