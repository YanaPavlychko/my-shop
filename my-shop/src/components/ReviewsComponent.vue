<template>
  <div>
    <h2>Відгуки</h2>

    <label for="ratingFilter">Фільтрувати за рейтингом:</label>
    <select id="ratingFilter" v-model="selectedRating">
      <option value="">Всі</option>
      <option value="5">5 зірок</option>
      <option value="4">4 зірки</option>
      <option value="3">3 зірки</option>
      <option value="2">2 зірки</option>
      <option value="1">1 зірка</option>
    </select>

    <table>
      <thead>
        <tr>
          <th>Ім'я</th>
          <th>Рейтинг</th>
          <th>Коментар</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(review, index) in filteredReviews" :key="index">
          <td>{{ review.Name }}</td>
          <td>{{ review.Rating }}</td>
          <td>{{ review.Comment }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import Papa from "papaparse";

export default {
  data() {
    return {
      reviews: [], // Всі відгуки
      selectedRating: "", // Обраний рейтинг для фільтрації
    };
  },

  computed: {
    // Фільтруємо відгуки за обраним рейтингом
    filteredReviews() {
      if (!this.selectedRating) {
        return this.reviews; // Якщо рейтинг не вибрано, показуємо всі відгуки
      }
      return this.reviews.filter(
        (review) => review.Rating === this.selectedRating
      );
    },
  },

  created() {
    const csvContent = `
Name,Rating,Comment
Іван,5,Дякую за швидку доставку
Ольга,5,Все супер! Буду замовляти ще
Андрій,5,Обслуговування, як завжди - на висоті
Марина,4,Все чудово! Покупкою задоволена, але коробка була прим'ята.
Сергій,5,Рекомендую цей чудовий магазин усім!
Данило,5,Дуже демократичні ціни. Я завжди купую лише тут.
Матвій,5,Дякую за подарунок до покупки - завжди радуєте приємними сюрпризами.
Анна,5,Дякую за чудові знижки
Раймонд,4,Як завжди все кльово, але малий термін гарантії для годинника, хотілося б довше.
    `;
    Papa.parse(csvContent.trim(), {
      header: true,
      complete: (result) => {
        this.reviews = result.data; // Завантажуємо дані у масив
      },
    });
  },
};
</script>
  
  <style scoped>
h2 {
  text-align: center;
}
table {
  width: 90%;
  margin: 30px auto;
}
th,
td {
  background: #f8f9fa;
  padding: 4px;
}
</style>
  















  
  