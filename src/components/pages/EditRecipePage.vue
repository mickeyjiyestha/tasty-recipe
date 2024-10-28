<template>
  <main>
    <div class="container-md my-5 py-5">
      <recipe-form
        v-if="detailData && !isLoading"
        :recipeData="detailData"
        :isEdit="true"
      />
    </div>
  </main>
</template>

<script setup>
import RecipeForm from "../recipeForm/RecipeForm.vue";
import { ref, onMounted } from "vue";
import { useStore } from "vuex";
import { useRoute } from "vue-router";

const store = useStore();
const route = useRoute();
const detailData = ref({});
const isLoading = ref(false);

onMounted(async () => {
  isLoading.value = true;
  const recipeId = route.params.id;

  // Fetch recipe details based on ID
  await store.dispatch("recipe/getRecipeDetail", recipeId);

  // Assign the fetched data to `detailData`
  detailData.value = store.state.recipe.recipeDetail;
  isLoading.value = false;
});
</script>
