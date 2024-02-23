<template>
  <div class="recipe">
    <img :src="item.image" alt="" />
    <div>
      <h3>{{ item.name }}</h3>
      <p>Difficulty: {{ item.difficulty }}</p>
      <p>Cuisine: {{ item.cuisine }}</p>
      <p>Calories per Serving: {{ item.caloriesPerServing }}</p>
    </div>
    <div>
      <h4>Ingredients</h4>
      <ul>
        <li v-for="(ingredient, ind) in item.ingredients" :key="ind">
          {{ ingredient }}
        </li>
      </ul>
    </div>
  </div>
</template>
<script setup>
const { item } = defineProps({
  item: Object,
});
console.log(item);
</script>
<style lang="scss" scoped>
.recipe {
  box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1),
    0 8px 10px -6px rgb(0 0 0 / 0.1);
  border-radius: 25px;

  img {
    width: 100%;
    height: 176px;
    object-fit: cover;
    border-radius: 25px 25px 0 0;
  }

  div {
    padding: 12px;
    display: flex;
    flex-direction: column;
    gap: 10px;

    h3,
    h4 {
      font-weight: 700;
    }

    h3 {
      font-size: 16px;
    }

    h4 {
      font-size: 13px;
    }

    ul {
      padding: 0 18px;
    }

    p,
    li {
      font-size: 12px;
    }
  }

  div:last-of-type {
    gap: 3px;
  }
}
</style>
