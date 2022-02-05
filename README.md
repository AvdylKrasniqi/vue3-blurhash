# vue3-blurhash

[![NPM Version](https://img.shields.io/npm/v/vue3-blurhash.svg?style=flat)](https://www.npmjs.com/package/vue3-blurhash)
[![NPM Downloads](https://img.shields.io/npm/dm/vue3-blurhash.svg?style=flat)](https://npmcharts.com/compare/vue3-blurhash?minimal=true)

#### Inspired by [react blurhash](https://github.com/woltapp/react-blurhash)

# 
# 

> Vue components for using the [blurhash algorithm](https://blurha.sh) in your Vue projects

## Install

```sh
npm install --save blurhash vue3-blurhash
```

## Usage

```js
import { Blurhash } from "vue3-blurhash";
<template>
  <div id="app" style="height: 500px; width: 500px;">
    <vue3-blurhash src="https://blurha.sh/assets/images/img2.jpg" :punch="1" hash="LGF5]+Yk^6#M@-5c,1J5@[or[Q6." height="100%" width="100%" :resolutionX="10" :resolutionY="10"></vue3-blurhash>
  </div>
</template>

```

### Description


`Blurhash` component is the recommended way to render blurhashes in your Vue projects.
It uses `BlurhashCanvas` and a wrapping `div` to scale the decoded image to your desired size. 
You may control the quality of the decoded image with `resolutionX` and `resolutionY` props.

#### Props

| name                     | description                                                                                                                                                                  |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `src` (String)            | The source url of image (required)                                                                                      |
| `hash` (string)          | The encoded blurhash string.  (required)                                                                                                                                              |
| `width` (int \| string)  | Width (CSS) of the decoded image.                                                                                                                                            |
| `height` (int \| string) | Height (CSS) of the decoded image.                                                                                                                                           |
| `resolutionX` (int)      | The X-axis resolution in which the decoded image will be rendered at. Recommended min. 32px. Large sizes (>128px) will greatly decrease rendering performance. (Default: 32) |
| `resolutionY` (int)      | The Y-axis resolution in which the decoded image will be rendered at. Recommended min. 32px. Large sizes (>128px) will greatly decrease rendering performance. (Default: 32) |
| `punch` (int)            | Controls the "punch" value (~contrast) of the blurhash decoding algorithm. (Default: 1)                                                                                      |
#### Events

| name            | description                                                                             |
| --------------- | --------------------------------------------------------------------------------------- |
| imageLoaded     | Triggers when image is full loaded                                                      |

##### `<BlurhashCanvas />`


```js
import { BlurhashCanvas } from "vue3-blurhash";
```

### Description

`BlurhashCanvas` is the barebones implementation of a blurhash string to a canvas. You may want to use it instead of the `Blurhash` component e.g. if you want to control the scaling yourself.

#### Props

| name            | description                                                                             |
| --------------- | --------------------------------------------------------------------------------------- |
| `hash` (string) | The encoded blurhash string.                                                            |
| `width` (int)   | Width of the decoded image.                                                             |
| `height` (int)  | Height of the decoded image.                                                            |
| `punch` (int)   | Controls the "punch" value (~contrast) of the blurhash decoding algorithm. (Default: 1) |

#### Example

```jsx
<BlurhashCanvas hash="LEHV6nWB2yk8pyo0adR*.7kCMdnj" :width="400" :height="300" :punch="1" />
```

## Browser support

Blurhash depends on `Uint8ClampedArray`, which is supported on all mainstream browsers and >=IE11.
