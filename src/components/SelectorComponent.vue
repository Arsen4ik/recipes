<!-- :src="`../assets/arrow${startFrom >= 6 ? '' : '-disabled'}.svg`" -->

<!-- 
<div
:class="`arrow ${chosenNum + length > max && 'disabled'}`"
@click="
  chosenNum + length <= max &&
    emit('changeStartFrom', startFrom + length)
"
>
<img class="right-arrow" src="../assets/arrow.svg" alt="" />
</div> -->

<template>
  <div class="selector">
    <div
      :class="`arrow ${startFrom <= length && 'disabled'}`"
      @click="startFrom > length && emit('changeStartFrom', startFrom - length)"
    >
      <img class="left-arrow" src="../assets/arrow.svg" alt="" />
    </div>
    <div
      v-for="(_, ind) in new Array(length)"
      :key="ind"
      :class="ind + startFrom === chosenNum && 'selected'"
      @click="emit('changeNum', ind + startFrom)"
    >
      {{ ind + startFrom }}
    </div>
    <div
      :class="`arrow ${chosenNum + length > max && 'disabled'}`"
      @click="
        chosenNum + length <= max && emit('changeStartFrom', startFrom + length)
      "
    >
      <img class="right-arrow" src="../assets/arrow.svg" alt="" />
    </div>
    <!-- <div
      :class="`arrow ${
        cardsAmount * length <= (max / cardsAmount) * length && 'disabled'
      }`"
      @click="
        chosenNum * length <= (max / cardsAmount) * length &&
          emit('changeStartFrom', startFrom + length)
      "
    >
      <img class="right-arrow" src="../assets/arrow.svg" alt="" />
    </div> -->
    <!-- {{ length }}
    {{ cardsAmount }} -->
    <!-- {{ cardsAmount * length }}
    {{ max }}
    {{ (max / cardsAmount) * length }} -->
  </div>
</template>
<script setup>
const { chosenNum, length, startFrom, max, cardsAmount } = defineProps({
  chosenNum: Number,
  length: Number,
  startFrom: Number,
  max: Number,
  cardsAmount: Number,
});
const emit = defineEmits(["changeNum", "changeStartFrom"]);
</script>
<style lang="scss" scoped>
* {
  user-select: none;
}
.selector {
  padding: 35px 0;
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 16px;

  .selected {
    background-color: #185bc3;
    border: 1px solid #185bc3;
    color: white !important;
  }

  .disabled {
    opacity: 40%;

    &:hover {
      box-shadow: none;
      cursor: not-allowed;

      img {
        transform: none;
      }
      .left-arrow {
        transform: rotate(180deg);
      }
    }
  }

  div {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 64px;
    height: 64px;
    border: 1px solid #bdbdbd;
    border-radius: 6px;
    font-weight: 800;
    font-size: 18px;
    color: #bdbdbd;
    transition: all 0.25s ease-in-out;

    &:hover {
      box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1),
        0 2px 4px -2px rgb(0 0 0 / 0.1);
      cursor: pointer;
      color: #185bc3;

      img {
        transform: scale(1.25);
      }
      .left-arrow {
        transform: scale(1.25) rotate(180deg);
      }
    }

    img {
      width: 32px;
      height: 32px;
      transition: all 0.25s ease-in-out;
    }
    .left-arrow {
      transform: rotate(180deg);
    }
  }
}
</style>
