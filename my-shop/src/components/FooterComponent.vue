<template>
  <div>
    <footer>
      <p>Email: example@email.com</p>
      <p>Телефон: +380 00 000 0000</p>
      <a href="#">Про нас</a> |
      <a href="#">Доставка</a>
    </footer>
  </div>
</template>

<script>
export default {
  name: "FooterComponent",
};
</script>

<style scoped>

footer {
  background: #eee;
  padding: 20px;
  text-align: center;
  margin-top: 40px;
  
}
a {
  margin: 2px;
  color: blue;
  text-decoration: none;
}
</style>
