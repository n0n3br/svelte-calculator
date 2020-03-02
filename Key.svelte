<script>
  export let key;
  $: color = key.color ? `btn-${key.color}` : "btn-secondary";
</script>
<button class='btn {color} btn-block' on:click={() => key.click(key.label)}>
  {key.label}
</button>
<style>
  button {
    font-size: 30px;
    font-family: "VT323";
  }
</style>