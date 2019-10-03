<script>
  import { recipes } from "./recipes.js";
  import Recipe from "./recipe/Recipe.svelte";
</script>

{#each recipes as recipe}
  <Recipe {recipe} />
{/each}
