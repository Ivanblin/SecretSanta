<template>
  <div class="">
    <h1>Тайный санта</h1>
    <p>введите всех участницов</p>
    <div class="" v-if="error">
      <h2>Кому-то не достанеться подарок</h2>
      <p>Введите еще одного человека</p>
      <button @click="removePeople">Либо продолжить?</button> <br> <br>
    </div>
    <div class="" v-if="people">
      Для {{lastPeaple}} не хватило пары, найдите ему тайного санту <br> <br>
    </div>
    <div class="">
      <input v-model="name" type="text" @keyup.enter="addPeople">
      <button @click="addPeople">Add</button>
    </div>
    {{name}} <br>
    {{array}}

    <div class="">
      <button @click="clickResult">result</button> <br>
      {{result}}
    </div>

    <div class="" v-for="(item, index) of result" :key="index">
      <p>{{item}} и {{index}} стали друг для друга Тайными сантами</p>
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
      error: false,
      people: false,
      lastPeaple: ''
    }
  },
  methods: {
    clickResult () {
      let arr = this.array,
          result = {},
          arrayOne = [],
          arraytwo = [];

      // рандомно пересобираю массив
      arr = arr.sort(() => Math.random() - 0.5);

      if (arr.length % 2 !== 0) {
        this.error = true
        return
      }

      // Разбиваю 1 массив на 2 массива
      arr.forEach((item, index) => {
        if ((index + 1) % 2 == 0 ) {
          arrayOne.push(item);
        } else {
          arraytwo.push(item);
        }

      });
      // рандомно пересобираю массив arrayOne и arrayTwo
      arrayOne = arrayOne.sort(() => Math.random() - 0.5);
      arraytwo = arraytwo.sort(() => Math.random() - 0.5);

      arrayOne.forEach((key, i) => result[key] = arraytwo[i]);
      this.result = result
    },

    addPeople () {
      if (this.name == '' ) {
        return false
      } else {
        this.array.push(this.name)
      }
      this.name = ''
    },

    removePeople () {
      this.error = false
      this.array = this.array.sort(() => Math.random() - 0.5);
      let lastPeaple = this.array.pop()
      this.lastPeaple = lastPeaple
      this.people = true
    }
  }
}
</script>
