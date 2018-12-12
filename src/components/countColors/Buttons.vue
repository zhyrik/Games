<template>
  <div class="buttons">
    <div class="button red" @click="checkRed">Red</div>
    <div class="button" @click="checkBlue">Equally</div>
    <div class="button blue" @click="checkEqually">Blue</div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      point: 0
    }
  },
  props: ['red', 'blue', 'start'],
  methods: {
    checkRed () {
      if (this.red > this.blue) this.point ++
      this.start()
    },
    checkBlue () {
      if (this.red < this.blue) this.point ++
      this.start()
    },
    checkEqually () {
      if (this.red == this.blue) this.point ++
      this.start()
    }
  }
}
</script>

<style scoped>
.buttons{
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 45px;
  display: grid;
  grid-template-columns:1fr 1fr 1fr;
  grid-gap: 1%;
}
.button{
  border: 1px solid black;
  background: #111;
  color: white;
  font-weight: 700;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}
.red{
  background: red;
}
.blue{
  background: blue;
}
</style>