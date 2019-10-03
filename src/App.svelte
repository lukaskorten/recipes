<script>
  import { recipes } from "./recipes.js";
  import RecipeListItem from "./recipe/RecipeListItem.svelte";
  import Recipe from "./recipe/Recipe.svelte";
  import ShoppingList from "./shoppinglist/ShoppingList.svelte";
  import Hint from "./ui/Hint.svelte";

  let selectedRecipe;
  let shoppingList = [];

  function selectRecipe(recipe) {
    selectedRecipe = recipe;
  }
  function addToShoppingList(e) {
    const ingredients = e.detail.ingredients;
    shoppingList = [...shoppingList, ...ingredients];
  }
</script>

<style>
  header {
    height: 6rem;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #f9f9f9;
    color: #00695c;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
  }

  main {
    margin-top: 4rem;
  }

  .container {
    max-width: 90rem;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
  }

  .col:nth-of-type(1) {
    max-width: 25rem;
  }
  .col:nth-of-type(2) {
    width: 29rem;
  }
  .col:nth-of-type(3) {
    max-width: 25rem;
  }

  h2 {
    margin: 2rem 0;
    font-size: 1.2rem;
  }

  ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }
</style>

<header>
  <div class="container">
    <h1>Recipes</h1>
  </div>

</header>

<main>
  <div class="container">
    <div class="col">
      <h2>Rezept auswählen...</h2>
      <ul>
        {#each recipes as recipe}
          <li>
            <RecipeListItem {recipe} on:click={() => selectRecipe(recipe)} />
          </li>
        {/each}
      </ul>
    </div>
    <div class="col">
      <h2>Zutaten prüfen/ ändern ...</h2>
      {#if selectedRecipe}
        <Recipe {...selectedRecipe} on:toshoppinglist={addToShoppingList} />
      {:else}
        <Hint icon="file-alt">Bitte wähle ein Rezept aus</Hint>
      {/if}
    </div>
    <div class="col">
      <h2>Einkaufsliste</h2>
      <ShoppingList products={shoppingList} />
    </div>
  </div>
</main>
