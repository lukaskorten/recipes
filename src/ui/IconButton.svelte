<script>
  export let type = null;
  export let mode = "default";
  export let title = "";

  $: icon = type ? `fas fa-${type}` : "invisible";
</script>

<style>
  button {
    background: transparent;
    border: none;
    border-radius: 6px;
    transition: color 250ms cubic-bezier(0.075, 0.82, 0.165, 1);
    color: #afafaf;
    cursor: pointer;
  }

  button:hover {
    color: #00897b;
  }

  button.warning:hover {
    color: #fa9417;
  }
</style>

<button class={mode} on:click {title}>
  <i class={icon} />
  <slot />
</button>
