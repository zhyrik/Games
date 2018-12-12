<template>
  <div class="main">
    <div
      v-for="item in items"
      :key="item.index"
      :class="[item.color, item.forma]"
      class="item"
      :style="{ gridColumn: item.col, gridRow: item.row}"
    ></div>
    <my-buttons :red="red" :blue="blue" :start="start"></my-buttons>
  </div>
</template>

<script>
import Buttons from './Buttons'

export default {
  name: 'countColors',
  components: {
    myButtons: Buttons
  },
  data () {
    return {
      countItems: 15,
      red: null,
      blue: null,
      items: [],
      color: '',
      forma: '',
      arr: [],
      row: null,
      col: null
    }
  },
  methods: {
    randomColAndRow () {
      let col = Math.floor(Math.random() * 10) + 1
      let row = Math.floor(Math.random() * 4) + 1
      if (this.arr[row][col] == 2) {
        this.randomColAndRow ()
      } else {
        this.arr[row][col] = 2
        this.col = col
        this.row = row
      }
    },
    randomColor () {
      if (Math.random() < 0.5) {
          this.color = 'red'
          this.red++
        }
        else {
          this.color = 'blue'
          this.blue++
        }
    },
    rondomForma () {
      const random = Math.floor(Math.random() * 4)
      switch (random) {
        case 0:
          this.forma = 'star'
        break;
        case 1:
          this.forma = 'circle'
        break;
        case 2:
          this.forma = 'triengle'
        break;
        case 3:
          this.forma = 'square'
      }
    },
    createItems () {
      for (let i=0; i<this.countItems; i++) {
        this.randomColor()
        this.randomColAndRow()
        this.rondomForma()
        this.items.push({
          color: this.color,
          forma: this.forma,
          col: this.col,
          row: this.row,
          index: i
        })
      }
    },
    start () {
      this.items = []
      this.red = null
      this.blue = null
      this.col = null
      this.row = null
      this.arr = [
        [1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
        [1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
        [1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
        [1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
        [1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
        [1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
        [1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
      ]
      this.createItems()
      console.log(this.arr)
      console.log(this.items)
    }
  }
}
</script>

<style scoped>
.main{
  position: relative;
  display: grid;
  grid-template-columns:1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr 1fr 1fr 1fr;
  grid-gap: 4% 1%;
  width: 100%;
  height: 100%;
}
.star{
  clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
}
.circle{
  border-radius: 50%;
}
.triengle{
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
}
.square{
  clip-path: inset(0 2% 0 0);
}
.red{
  background: red;
}
.blue{
  background: blue;
}
</style>