<script setup>

import {tg} from "../main.js";


sessionStorage.removeItem('company')
sessionStorage.removeItem('members')



const clickNext = async () => {
  await fetch(`/api/v1/event_bot/subscriber/${tg.initDataUnsafe.user.id}`, {
    method: 'PATCH',
    headers: {
      "Content-Type": "application/json",
      // "Authorization": `Token ${config.DRF_API_TOKEN}`
    },
    body: JSON.stringify({
      "is_approve_mailing": true
    })
  })
}
</script>

<template>
  <div class="container">
    <div class="texts">
      <p class="text">
        Добрый день!<br>
        Вы приглашены<br>
        на презентацию нового масштабного проекта<br>
        ГК «ИНСИТИ».<br>
      </p>
      <p class="text">
        Чтобы подтвердить участие, заполните заявку в нашем
        чат-боте.
      </p>
    </div>
    <img class="logo" src="../../public/logo.png" alt="Логотип">
    <router-link @click="clickNext" class="button button__green" to="/registration-member">Подтвердить участие</router-link>

  </div>
</template>

<style scoped>
.container {
  background-image: url("../../public/bg.png");
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  height: 100%;
  background-color: #20343C;

}
.texts {
  padding: 27px 18px 80px 40px;
}
.text {
  margin-bottom: 40px;
  color: #fff;
  font-size: 20px;
  line-height: 26px;
  font-family: 'Montserrat', sans-serif;
}
.button {
  margin-bottom: 42px;
  background-color: #656A3E;
  font-family: 'Montserrat', sans-serif;
  font-size: 18px;
  line-height: 26px;
  font-weight: 400;
  max-width: 263px;
}
.logo {
  display: block;
  margin: 0 auto 65px;
  text-align: center;
  width: 183px;
}
</style>
