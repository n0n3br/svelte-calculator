<script>
  import Key from "./Key.svelte";
  export let keys;
</script>

<div class='row row-cols-4 mt-4 mb-4'>
  {#each keys as key (key.id)}
  <div class='col' >
    {#if key.label} 
      <Key key={key} />
    {/if}
  </div>
  {/each}
</div>

<style>
  .col {
    padding: 10px 5px;
  }
</style>