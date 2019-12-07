# VueJS + VueGL Globe Demo
![](https://s5.gifyu.com/images/ezgif.com-crope2161126fc9d94ca.gif)
### How to install and use
- `git clone https://github.com/FabianAhammer/DiploEarth.git`
- `cd DiploEarth`
- `npm i`
- `npm run serve`


### How does it work?
Starting off create a new Vue Project, basic options are enough for it to work.

Following that up, you need to *install* [three.js](https://www.npmjs.com/package/three), and [VueGL](https://www.npmjs.com/package/vue-gl) you can find the **VueGL Docs** [here](https://vue-gl.github.io/vue-gl/).

- `npm i three`
- `npm i vue-gl`

**VueGL is the Vue implementation of three.js.**

The next step is to open up the **main.js** and add

```javascript
import * as VueGL from "vue-gl";

Object.keys(VueGL).forEach(name => {
    Vue.component(name, VueGL[name]);
});
```
[Reference](https://github.com/FabianAhammer/DiploEarth/blob/master/src/main.js)

Afterwards, you can start adding in what you want.
For more details visit the [Docs](https://vue-gl.github.io/vue-gl/), 
I will add in an example for show.
```html
<vgl-renderer antialias style="height: 100vh;">
    <vgl-scene>
      <vgl-sphere-geometry name="sphere"  :width-segments="20" :height-segments="20"></vgl-sphere-geometry>
      <vgl-mesh-standard-material name="std"></vgl-mesh-standard-material>
      <vgl-mesh geometry="sphere" material="std"></vgl-mesh>
      <vgl-ambient-light color="#ffeecc"></vgl-ambient-light>
      <vgl-directional-light position="0 1 2"></vgl-directional-light>
    </vgl-scene>
    <vgl-perspective-camera orbit-position="200 1 0.5"></vgl-perspective-camera>
  </vgl-renderer>
```

##### Important ending Notes, that helped me

In order to load in Images as [VglTexture](https://vue-gl.github.io/vue-gl/components/textures/vgl-texture.html#content-wrapper) one needs to require them, to get them loaded beforehand.

```html
...
<vgl-texture :src="require('../assets/earth.jpg')" center="0 0" name="texture"></vgl-texture>
...
```
