<template>
  <div>
    <select required v-model="localSelectorLength">
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
      <option value="4">4</option>
      <option value="5">5</option>
      <option value="6">6</option>
      <option value="7">7</option>
      <option value="8">8</option>
      <option value="9">9</option>
      <option value="10">10</option>
    </select>
    <select required v-model="localCardsAmount">
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
      <option value="4">4</option>
      <option value="5">5</option>
      <option value="6">6</option>
      <option value="7">7</option>
      <option value="8">8</option>
      <option value="9">9</option>
    </select>
  </div>
</template>
<script setup>
import { ref, watch } from "vue";
const { selectorLength, cardsAmount } = defineProps({
  selectorLength: Number,
  cardsAmount: Number,
});
const emit = defineEmits(["changeSelectorLength", "changeCardsAmount"]);

let localSelectorLength = ref(selectorLength);
let localCardsAmount = ref(cardsAmount);

watch(localSelectorLength, (newVal) => {
  //   console.log(+newVal);
  emit("changeSelectorLength", +newVal);
});
watch(localCardsAmount, (newVal) => {
  console.log(+newVal);
  emit("changeCardsAmount", +newVal);
});
</script>
<style lang="scss" scoped></style>
