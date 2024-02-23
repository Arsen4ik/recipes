<template>
  <section>
    <h1>Recipes</h1>
    <!-- <change-selector
      :selectorLength="selectorLength"
      :cardsAmount="cardsAmount"
      @changeSelectorLength="changeSelectorLength"
      @changeCardsAmount="changeCardsAmount"
    ></change-selector> -->
    <selector-component
      v-if="recipes.length"
      :chosenNum="chosenNum"
      :startFrom="startFrom"
      :length="selectorLength"
      :cardsAmount="cardsAmount"
      :max="recipes.length"
      @changeNum="changeNum"
      @changeStartFrom="changeStartFrom"
    ></selector-component>
    <p v-else class="loader">🌀</p>
    <!-- {{ chosenNum }}
    {{ recipes.length }} -->
    <!-- {{ chosenNum }} <br />
    {{ (chosenNum - 1) * 6 }} - {{ chosenNum * 6 - 1 }} -->
    <!-- <pre>{{ recipes }}</pre> -->
    <!-- 
    {{
      recipes.slice(
        (chosenNum - 1) * cardsAmount,
        (chosenNum - 1) * cardsAmount + cardsAmount
      )
    }} -->
    <recipe-list
      :list="
        recipes.slice(
          (chosenNum - 1) * cardsAmount,
          (chosenNum - 1) * cardsAmount + cardsAmount
        )
      "
    ></recipe-list>
  </section>
</template>
<script setup>
import { onMounted, reactive, ref } from "vue";
import SelectorComponent from "./components/SelectorComponent.vue";
import RecipeList from "./components/RecipeList.vue";
import ChangeSelector from "./components/ChangeSelector.vue";

let cardsAmount = ref(6);

let recipes = reactive([]);

let chosenNum = ref(1);
let startFrom = ref(1);
let selectorLength = ref(5);

const changeSelectorLength = (newNum) => {
  selectorLength.value = newNum;
};
const changeCardsAmount = (newNum) => {
  cardsAmount.value = newNum;
};

const changeNum = (newNum) => {
  chosenNum.value = newNum;
};
const changeStartFrom = (newNum) => {
  chosenNum.value = newNum;
  startFrom.value = newNum;
};

onMounted(async () => {
  // console.time();
  const res = await fetch("https://dummyjson.com/recipes");
  const data = await res.json();
  recipes.push(...data.recipes);
  // console.timeEnd();
});
</script>
<style lang="scss" scoped>
h1 {
  padding: 35px 0;
  text-align: center;
  font-size: 48px;
}
.loader {
  text-align: center;
  font-size: 70px;
  padding: 50px;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>
