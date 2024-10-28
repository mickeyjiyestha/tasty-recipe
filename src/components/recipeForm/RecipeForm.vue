<template>
  <ul class="list-group">
    <recipe-form-header></recipe-form-header>
    <recipe-form-body
      :isEdit="isEdit"
      :recipeData="recipeData"
    ></recipe-form-body>
  </ul>
</template>

<script setup>
import RecipeFormHeader from "./RecipeFormHeader.vue";
import RecipeFormBody from "./RecipeFormBody.vue";
import { defineProps } from "vue";

const props = defineProps({
  isEdit: {
    type: Boolean,
    default: false,
  },
  recipeData: {
    type: Object,
    required: true,
  },
});
</script>
