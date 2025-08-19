<template>
  <div class="login-container">
    <h2>Авторизація</h2>
    <input  v-model="username" placeholder="Логін" />
    <input type="password" v-model="password" placeholder="Пароль" />
    <button v-on:click="login">Увійти</button>
    <p v-if="message" class="error">{{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: "",
      password: "",
      message: "",
      users: []
    };
  },

  async mounted() {
    try {
      const response = await fetch("/admin.json");
      if (!response.ok) {
        throw new Error("HTTP помилка: " + response.status);
      }
      this.users = await response.json();
    } catch (error) {
      console.error("Помилка завантаження JSON: " + error);
      this.message = "Помилка сервера! Спробуйте пізніше.";
    }
  }
};

</script>

<style>
</style>