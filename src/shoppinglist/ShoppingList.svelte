<script>
  import Product from "./Product.svelte";
  import Hint from "../ui/Hint.svelte";
  export let products;
</script>

<style>
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
</style>

{#if products && products.length > 0}
  <ul>
    {#each products as product}
      <li>
        <Product title={product.description} />
      </li>
    {/each}
  </ul>
{:else}
  <Hint icon="pepper-hot">
    Leer hier. Füge deiner Einkaufsliste ein Paar Lebensmittel hinzu
  </Hint>
{/if}
