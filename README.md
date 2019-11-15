# VueJS + VueGL Globe Demo

### How to install and use
- `git clone https://github.com/FabianAhammer/DiploEarth.git`
- `cd DiploEarth`
- `npm i`
- `npm run serve`

### Public Demo
https://fabianahammer.github.io/

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
[reference](https://github.com/FabianAhammer/DiploEarth/blob/master/src/main.js)
