<template>
<div class="container">
    <div class="sample">
        <button class="btn btn-success mt-2" v-on:click="show = !show">{{btnText}}</button>
        <hr>
        <Progress v-bind:val="sum" v-bind:max="maxNumbers * 5"></Progress>
        <h2 v-show="show">Your profit is {{sum}}</h2>
        <hr>
        <Progress v-bind:val="numbers.length" v-bind:max="maxNumbers"></Progress>
        <hr>
        <button class="btn btn-success mb-2" v-on:click="addNumber" v-bind:disabled="done">Add number</button>
        <ul class="list-group">
            <li class="list-group-item" v-for="number in numbers" :key="number.id">{{number}}</li>
        </ul>
    </div>
</div>
</template>

<script>
import Progress from './components/Progress'

export default {
  name: "App",
  data() {
    return {
      show: true,
      numbers: [],
      maxNumbers: 10
    }
  },
  methods: {
    addNumber() {
      if (!this.done) {
        let number = Math.floor(Math.random() * 11) - 5;
        this.numbers.push(number);
      }
    }
  },
  computed: {
    sum() {
      let sum = 0;
      for (let i = 0; i < this.numbers.length; i++) {
        const element = this.numbers[i];
        sum += element;
      }
      return sum;
    },
    btnText() {
      return this.show ? "Hide resualt" : "Show resualt";
    },
    done() {
      return this.numbers.length >= this.maxNumbers;
    }
  },
  components: {
    Progress
  }
};
</script>

<style>
</style>
