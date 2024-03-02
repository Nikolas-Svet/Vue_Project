<!-- Первый файл -->
<template>
  <div>
    <div class="hello">
      <h1>{{ msg }}</h1>
      <button v-on:click="handleClick">Информация обо мне</button>
      <transition name="feedback">
        <h1 v-if="flag">{{ info }}</h1>
      </transition>
    </div>
    <img src="../assets/Логотип_КемГУ.png" alt="logo" class="logo">
    <footer>
      <a href="https://vk.com/nik.svetkin">Контакты со мной: example@example.com</a>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      show: true,
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
      this.flag = !this.flag; // Инвертируем значение флага
    }
  }
}

</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
}

footer {
  background-color: #333;
  color: #2c3e50;
  text-align: center;
  height: 80px;
  position: fixed;
  bottom: 0;
  margin: 0 0 0 -10px;
  width: 100%;
}

.logo {
  position: fixed;
  bottom: 100px;
  right: 120px;
  height: 250px;
}

a {
  color: white;
}

.feedback-enter-active,
.feedback-leave-active {
  transition: opacity 0.5s ease;
}

.feedback-enter-from,
.feedback-leave-to {
  opacity: 0;
}

</style>
