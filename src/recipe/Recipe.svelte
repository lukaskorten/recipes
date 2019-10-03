<script>
  import Ingredient from "./Ingredient.svelte";
  import Button from "../ui/Button.svelte";
  import IconButton from "../ui/IconButton.svelte";
  import IngredientInput from "./IngredientInput.svelte";

  let ingredients = [
    { amount: 50, unit: "g", description: "Butter" },
    { amount: 250, unit: "g", description: "Mehl" },
    { amount: 80, unit: "g", description: "Zucker" },
    { amount: 2, unit: "TL", description: "Backpulver" },
    { amount: 0.5, unit: "TL", description: "Salz" },
    { amount: 300, unit: "ml", description: "Milch" },
    { amount: 1, description: "Ei" },
    { amount: 2, unit: "EL", description: "Öl" }
  ];

  function addIngredient(e) {
    console.log(e);
    const ingredient = { ...e.detail };
    ingredients = [...ingredients, ingredient];
  }

  function removeIngredient(e) {
    console.log(e);
    const ingredientName = e.detail;
    ingredients = ingredients.filter(
      ingredient => ingredient.description !== ingredientName
    );
  }
</script>

<style>
  .recipe {
    width: 25rem;
    border-radius: 0.5rem;
    padding: 1rem 2rem;
    box-shadow: 0 15px 25px -10px rgba(0, 0, 0, 0.15);
    background: #fefefe;
  }

  h2 {
    margin: 1rem 0 2rem 0;
    color: #00695c;
  }

  ul {
    padding: 0;
    list-style: none;
    color: #616161;
    margin: 0 0 2rem;
  }

  li {
    padding: 0;
  }

  .ingredients-footer {
    display: flex;
    justify-content: center;
  }

  .footer {
    display: flex;
    justify-content: center;
    padding-top: 1rem;
    margin-top: 1rem;
    box-shadow: 0 -15px 20px -25px rgba(0, 0, 0, 0.25);
  }
</style>

<div class="recipe">
  <h2>American Pancakes</h2>
  <ul>
    {#each ingredients as ingredient}
      <li>
        <Ingredient {...ingredient} on:remove={removeIngredient} />
      </li>
    {/each}
  </ul>
  <IngredientInput on:save={addIngredient} />
  <div class="ingredients-footer">
    <IconButton>Zutat hinzufügen</IconButton>
  </div>
  <div class="footer">
    <Button>Auf die Einkaufsliste</Button>
  </div>
</div>
