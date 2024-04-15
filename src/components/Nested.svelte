<script>
    let showImage = false;
</script>

<main>
    <h1>A quickly nested component.</h1>
    <button on:click={() => showImage = !showImage}>What's inside?</button>

    {#if showImage}
        <img src="nesquick.jpeg" alt="nesquick" />
    {/if}
</main>

<style>
    button {
      margin: 1rem;
      padding: 0.5rem 1rem;
      border: none;
      border-radius: 4px;
      background-color: #007bff;
      color: white;
      cursor: pointer;
    }
    main {
      border: 1px solid black;
      padding: 1rem;
      margin: 1rem;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }

</style>
