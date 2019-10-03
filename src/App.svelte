<script>
  import { recipes } from "./recipes.js";
  import Recipe from "./recipe/Recipe.svelte";

  const pancakes = recipes[0];
</script>

<Recipe recipe={pancakes} />
