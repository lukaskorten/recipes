<script>
  import { createEventDispatcher } from "svelte";

  let description;
  let amount;
  let unit;

  const dispatch = createEventDispatcher();

  function save() {
    console.log("Form wurde submitted!");
    const ingredient = { description, amount, unit };
    dispatch("save", ingredient);
  }
</script>

<style>
  form {
    margin: 0;
  }
  input[type="submit"] {
    display: none;
  }

  section {
    background: #ffffff;
    box-shadow: 0 3px 8px -3px rgba(0, 0, 0, 0.15);
    border-radius: 0.5rem;
    padding: 1rem;
    display: flex;
    justify-content: space-between;
    margin: 0 -1rem 1rem;
  }

  input,
  select {
    border: 2px solid #f5f5f5;
    outline: none;
    border-radius: 6px;
    background: #f5f5f5;
    padding: 0.5rem 0.75rem;
    color: #616161;
    margin: 0;
  }

  input:focus,
  select:focus {
    background: #fafafa;
  }

  input::placeholder {
    opacity: 0.4;
  }

  .description {
    flex-grow: 1;
  }

  .amount,
  select {
    width: 5rem;
    margin-left: 0.5rem;
  }
</style>

<form on:submit|preventDefault={save}>
  <section>
    <input
      bind:value={description}
      class="description"
      type="text"
      placeholder="Was fehlt noch?" />
    <input bind:value={amount} class="amount" type="number" placeholder="100" />
    <select bind:value={unit}>
      <option value="g">g</option>
      <option value="ml">ml</option>
      <option value="TL">TL</option>
      <option value="Stck">Stck</option>
    </select>
  </section>
  <input type="submit" />
</form>
