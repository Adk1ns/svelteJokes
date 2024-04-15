<script>
    import { onMount } from 'svelte';
    import { jokes } from '../stores/store.js';
    import { tweened } from 'svelte/motion';
    import LaughMeter from '../components/LaughMeter.svelte';
  
    let joke = '';
    let progress = tweened($jokes.length);
  
    async function fetchJoke() {
      const response = await fetch('https://icanhazdadjoke.com/', {
        headers: { 'Accept': 'application/json' }
      });
      const data = await response.json();
      joke = data.joke;
  
      // @ts-ignore
      jokes.update(currentJokes => {
        progress.set(currentJokes.length + 1);
        return [...currentJokes, joke];
      });
    }
    if ($jokes.length < 1) {
        onMount(fetchJoke);
    }
  </script>
  
  <main>
    <h1>Joke of the Day App</h1>
    <p>New Joke: {joke}</p>
    <button on:click={fetchJoke}>Get New Joke</button>
    {#each $jokes as joke, index}
      <p>{index + 1}. {joke}</p>
    {/each}

    <LaughMeter {progress} />
    
  </main>

  <style>
    main {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      font-family: Arial, sans-serif;
    }
  
    h1 {
      margin-bottom: 1rem;
    }
  
    button {
      margin: 1rem;
      padding: 0.5rem 1rem;
      border: none;
      border-radius: 4px;
      background-color: #007bff;
      color: white;
      cursor: pointer;
    }
  
    button:hover {
      background-color: #0056b3;
    }
  
    p {
      margin: 0.5rem;
      width: 60rem;
      text-align: center;
    }
  
    h4 {
      margin-top: 2rem;
    }
  </style>