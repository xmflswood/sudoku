<template>
  <div style="width: 380px;">
    <div v-for="(h, index) in data">
      <span v-for="i in h">{{i}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'sudoku',
  data () {
    return {
      data: [
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0]
      ],
      num: 0,
      h: 0,
      v: 0
    }
  },
  methods: {
    cc () {
      this.num = Math.floor(Math.random()*9+1)
      if (this.check()) {
        this.data[this.h].splice(this.v ,1 ,this.num)
        if (this.h < 8) {
          this.h++
        } else {
          this.h = 0
          if (this.v < 8) {
            this.v++
          } else {
            return true
          }
        }
      } else {
        this.cc()
      }
    },
    check () {
      if (this.check33() && this.checkH() && this.checkV()) {
        return true
      } else {
        return false
      }
    },
    check33 () {
      var h = Math.floor(this.h / 3) * 3
      var v = Math.floor(this.v / 3) * 3
      for (let i = h; i < h + 3; i++) {
        for (let ii = v; ii < v + 3; ii++) {
          console.log(this.h, this.v)
          if ((i !== this.h && ii !== this.v) && this.data[i][ii] === this.num) {
            return false
          }
        }
      }
      return true
    },
    checkH () {
      for (let i = 0; i < 9; i++) {
        if (i !== this.v && this.data[this.h][i] === this.num) {
          return false
        }
      }
      return true
    },
    checkV () {
      for (let i = 0; i < 9; i++) {
        if (i !== this.h && this.data[i][this.v] === this.num) {
          return false
        }
      }
      return true
    }
  }
}
</script>
<style scoped>
  span {
    display: inline-block;
    width: 40px;
    height: 40px;
    line-height: 40px;
    border: 1px solid black;
  }
</style>
