<template>
  <div class="">
    <div class="">
      <input v-model="name" type="text">
      <button @click="click">Add</button>
    </div>
    {{name}} <br>
    {{array}}
    <div class="">
      <h1>result</h1>
      <button @click="clickResult">result</button>
    </div>
    {{result}}<br>

    <div class="">
      {{arrayTest}} <br>
      <button @click="clickTest">result</button> <br>
      {{resultTest}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'Santa',
  data () {
    return {
      name: '',
      array: [],
      result: {},
      arrayTest: ['Аня', 'Леша', 'Таня', 'Ваня', 'Анжела', 'Марк', 'Глория', 'Симонс'],
      resultTest: {}
    }
  },
  methods: {
    clickTest () {
      let arrayOne = [];
      let arraytwo = [];
      if (this.arrayTest.length % 2 !== 0) {
          console.log('dsfdf')
        }
      this.arrayTest.forEach((item, index) => {
        if ((index + 1) % 2 == 0 ) {
          arrayOne.push(item);
        } else {
          arraytwo.push(item);
        }

      });
      arrayOne = arrayOne.sort(() => Math.random() - 0.5);
      arraytwo = arraytwo.sort(() => Math.random() - 0.5);

      arrayOne.forEach((key, i) => this.resultTest[key] = arraytwo[i]);
      this.result = this.resultTest
      console.log(this.resultTest)
    },
    click () {
      if (this.name == '' ) {
        return false
      } else {
        this.array.push(this.name)
      }
      this.name = ''
    },
    clickResult () {
      console.log('asdasd')
    }
  }
}
</script>
