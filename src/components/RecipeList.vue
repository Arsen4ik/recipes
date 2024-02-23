<template>
  <div class="recipe-list" v-if="list.length">
    <recipe-item v-for="item in list" :key="item.id" :item="item"></recipe-item>
    <!-- <pre>{{ list }}</pre> -->
  </div>
  <p v-else class="empty">
    "сначала я сделал так, чтобы при больших списках можно было бы переходить по
    стрелочкам ➡️, но потом я понял, что рецептов тут не так много, а механизм
    удалять жалко, поэтому решил оставить 😎"
  </p>
</template>
<script setup>
import RecipeItem from "./RecipeItem.vue";
const { list } = defineProps({
  list: Array,
});
</script>
<style lang="scss" scoped>
.recipe-list {
  width: 772px;
  display: grid;
  margin: auto;
  padding: 40px 0;
  justify-content: space-between;
  grid-template-columns: repeat(3, 1fr);
  grid-column-gap: 50px;
  grid-row-gap: 40px;
}
.empty {
  padding: 100px 25%;
  text-align: center;
  font-size: xx-large;
  font-weight: 500;
}
</style>
