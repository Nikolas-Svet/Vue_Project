<template >
  <div class="hello test">
    <h1>{{ msg }}</h1>
    <button v-on:click="handleClick">Информация обо мне</button>
    <h1 v-if="flag"> {{ info }}</h1>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      info: "Меня зовут Светкин Никита Евгеньечи. \n " +
          "Являюсь студентом второго курса. \n Учусь на направлении \"Фундаментальная информатика и информационные технологии\"" +
          " в группе ФИТ-221.",
      flag: false
    };
  },
  props: {
    msg: String
  },
  methods: {
    handleClick() {
      this.flag = true
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.test {
  background-color: #808080;
}
</style>
