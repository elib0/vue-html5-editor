<style>
.vue-html5-editor .color-card {
  margin: 2px;
  width: 30px;
  height: 30px;
  float: left;
  cursor: pointer;
}
</style>
<template>
  <div>
    <label>
      <input type="radio" value="foreColor" v-model="command">&nbsp;
      {{$parent.locale["fore color"]}}
    </label>
    <label>
      <input type="radio" value="backColor" v-model="command">&nbsp;
      {{$parent.locale["background color"]}}
    </label>
  </div>
  <div>
    <color-picker @change-color="onChangeColor" :colors.sync="color"></color-picker>
  </div>
</template>
<script>
import { Sketch } from 'vue-color'

var defaultProps = {
  hex: '#194d33',
  hsl: {
    h: 150,
    s: 0.5,
    l: 0.2,
    a: 1
  },
  hsv: {
    h: 150,
    s: 0.66,
    v: 0.30,
    a: 1
  },
  rgba: {
    r: 25,
    g: 77,
    b: 51,
    a: 1
  },
  a: 1
}
export default {
  data(){
    return {
      command: "foreColor",//backColor
      color: defaultProps
    }
  },
  methods: {
    onChangeColor: function (val) {
      console.log(val)
    }
  },
  watch:{
    color (val, oldVal) {
      // console.log(val,oldVal)
      // this.$parent.execCommand(this.command, val.hex)
    }
  },
  components: {
    'color-picker': Sketch
  }
}
</script>