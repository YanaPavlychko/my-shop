<template>
  <div>
    <nav>
      <router-link to="/admin/products" active-class="active-link">
        Головна</router-link
      >

      <router-link to="/admin/reviews" active-class="active-link">
        Відгуки</router-link
      >
    </nav>

    <!-- Контент адміністративної панелі -->
    <main>
      <router-view />
      <!-- Динамічне завантаження сторінок -->
    </main>
  </div>
</template>

<script>
export default {
  name: "AdminDashboard",
};
</script> 

<style scoped>
nav a {
  background: #007bff;
  color: white;
  padding: 8px 16px;
  border-radius: 6px;
  text-decoration: none;
}

nav a:hover {
  background: #0056b3;
}

nav a.active-link {
  background: #28a745;
}

nav {
  display: flex;
  gap: 10px;
}
</style>