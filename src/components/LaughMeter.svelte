<script>
    export let progress
</script>

<main>
    <h4>Laugh-O-Meter</h4>
    <progress value={$progress} max="6"></progress>
    {#if $progress > 5}
      <h1>😂</h1>
    {:else if $progress > 4}
      <h1>😆</h1>
    {:else if $progress > 3}
      <h1>😄</h1>
    {:else if $progress > 2}
      <h1>😁</h1>
    {:else if $progress > 1}
      <h1>🙂</h1>
    {:else if $progress > 0}
      <h1>😐</h1>
    {:else}
      <h1>😑</h1>
    {/if}
</main>

<style>
    main {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      font-family: Arial, sans-serif;
    }
</style>