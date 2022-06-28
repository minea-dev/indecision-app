<template>
  <h2>{{ costumTitle}}</h2>
  <p>{{counter}} <sup>2</sup> = {{getSquareValue}} </p>
  <div>
      <button @click="increase">+1</button>
      <button @click="decrease">-1</button>
  </div>
</template>

<script>
export default {
    name: 'Counter',
    props:{
        title: String,
        start: {
            type: Number,
            default: 0,
            validator(value){
                return value > -1
            }
        }
    },
    data() {
        return {
            counter: this.start
        }
    },
    methods: {
        // increase
        increase() {
            this.counter+=1
        },
        // decrease
        decrease() {
            this.counter-=1
        }
    },
    computed: {
        // necesitamos que se actualice automáticamente
        getSquareValue() {
            return this.counter * this.counter
        },
        costumTitle(){
            return this.title || 'Counter'
        }
    }
}
</script>

<style>
button{
    background-color: #64B687;
    border-radius: 5px;
    border: 1px solid white;
    color: white;
    cursor: pointer;
    margin: 0 5px;
    padding: 5px 15px;
    transition: 0.3s ease-in-out;
}
button:hover {
    background-color: #5aa67b;
    transition: 0.3s ease-in-out;
}
</style>