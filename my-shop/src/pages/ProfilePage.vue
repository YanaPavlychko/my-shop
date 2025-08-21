<template>
  <div class="admin-container">
    <h2>Адмін-панель</h2>
    <p>Вітаємо, {{ username }}!</p>

    <div class="profile-card">
      <img
        :src="photo"
        width="200px"
        alt="Фото профілю"
        class="profile-photo"
        v-if="photo"
      />
      <p><strong>Ім'я:</strong> {{ name }}</p>
      <p><strong>Роль:</strong> {{ role }}</p>
      <p><strong>Телефон:</strong> {{ phone }}</p>
      <p><strong>Email:</strong> {{ email }}</p>
    </div>

    <button v-on:click="logout">Вийти</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: "",
      name: "Завантаження...",
      role: "Завантаження...",
      phone: "Завантаження...",
      email: "Завантаження...",
      photo: "", // Додаємо поле для фото
    };
  },

  mounted() {
    const savedUser = localStorage.getItem("authUser");
    if (savedUser) {
      this.username = JSON.parse(savedUser).name;
    } else {
      this.$router.push("/login");
      return;
    }

    const currentUser = JSON.parse(savedUser);

    this.name = currentUser.name;
    this.role = currentUser.role;

    this.phone = currentUser.phone;

    this.email = currentUser.email;

    this.photo = currentUser.photo || "default-photo.png";
  },

  methods: {
    logout() {
      localStorage.removeItem("authUser");
      this.$router.push("/");
    },
  },
};
</script>

  <!-- Приклад д/з -->
  <style>
.admin-container {
  max-width: 400px;
  margin: 50px auto;
  text-align: center;
}
button {
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
}
</style> 