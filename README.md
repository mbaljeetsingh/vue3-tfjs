# vue3-tfjs

This repo uses show how machine learning works directly in the web browser via TensorFlow.js to classify and detect common objects using the Object detection model (coco-ssd) from a live webcam stream. This is a sample vue 3 + vite project.

It actually gives the coordinates of the bounding box for each object which I was able to highlight using #canvas in the actual video stream.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
