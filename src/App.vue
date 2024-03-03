<template>
  <div>
    <div class="container">
      <h1 class="size_default">Приветствую, пользователь!</h1>
      <button v-on:click="handleClick_personal_info">Информация обо мне</button>
      <transition name="feedback">
        <h1 class="size_default" v-if="flag_pers_info">{{ info_pers_info }}</h1>
      </transition>
      <h1 class="size_default"></h1>
      <button v-on:click="handleClick" class="second-button">Данные с сервера</button>
      <transition name="feedback">
        <div v-if="flag_info" class="size_default">
          <h2 class="size_default">Информация о языках программирования и фреймворках:</h2>
          <ul class="size_default">
            <li class="size_default" v-for="(item, index) in info" :key="index">
              <strong>Язык программирования:</strong> {{ item['Language prog'] }}, <strong>Фреймворк:</strong> {{ item.Framework }}
            </li>
          </ul>
        </div>
      </transition>
    </div>
    <img src="@/assets/Логотип_КемГУ.png" alt="logo" class="logo">
    <footer class="footer_">
      <a class="footer_a">Обратная связь со мной:</a>
      <a  class="footer_a" href="https://vk.com/nik.svetkin">VK</a>
      <a class="footer_a">nikitaswetckin@mail.ru</a>
      <a class="footer_a">Telegram: @Nikolas_Svet</a>
    </footer>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      flag_pers_info: false,
      flag_info: false, // Переменная для управления отображением информации
      info: {}, // Пустой объект для хранения данных с сервера
      info_pers_info: "Меня зовут Светкин Никита Евгеньечи. " +
        "Являюсь студентом второго курса. Учусь на направлении \"Фундаментальная информатика и информационные технологии\"" +
        " в группе ФИТ-221. Я оформил данные, которые будут браться с сервера в форме ознакомления. Там перечислены навыки," +
          "которые я успел освоить",
    };
  },
  methods: {
    async handleClick() {
      try {
        // Запрос данных с сервера
        const response = await axios.get('http://localhost:3000/data');
        // Сохранение полученных данных
        this.info = response.data;
        // Устанавливаем флаг в true, чтобы отобразить информацию
        this.flag_info = true;
      } catch (error) {
        console.error('Ошибка при загрузке данных:', error);
      }
    },
    handleClick_personal_info() {
      this.flag_pers_info = !this.flag_pers_info; // Инвертируем значение флага
    }
  }
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}

footer {
  background-color: #333;
  color: #2c3e50;
  text-align: center;
  height: 40px;
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

button {
    margin: 15px 0 0 0 ;
    background-color: #333;
    color: white;
    border: 1px solid black;
    width: 100px;
    height: 50px;
    border-radius: 5px; /* Добавление закругленных углов */
    font-size: 16px; /* Установка размера шрифта */
    cursor: pointer; /* Изменение курсора при наведении */
}


.feedback-enter-active,
.feedback-leave-active {
  transition: opacity 0.5s ease;
}

.feedback-enter-from,
.feedback-leave-to {
  opacity: 0;
}

.size_default {
  margin: 15px 0 0 0 ;
  font-size: 25px;
}

.container {
  width: 1000px; /* Ширина контейнера */
  margin: 0 auto; /* Центрирование контейнера по горизонтали */
  padding: 20px; /* Поля вокруг текста */
  box-sizing: border-box; /* Учитываем ширину границы в общей ширине контейнера */
  text-align: center; /* Выравнивание текста по центру */
}

.footer_ {
  padding: 20px;
}

.footer_a {
  margin: 0 10px;
}


</style>


