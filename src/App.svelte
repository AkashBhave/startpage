<script lang="ts">
  import { onMount } from "svelte";

  let time = new Date();

  $: hours = time.getHours();
  $: minutes = time.getMinutes();
  $: seconds = time.getSeconds();

  $: timeString =
    String(hours).padStart(2, "0") +
    ":" +
    String(minutes).padStart(2, "0") +
    ":" +
    String(seconds).padStart(2, "0");

  onMount(() => {
    const interval = setInterval(() => {
      time = new Date();
    }, 1000);

    return () => {
      clearInterval(interval);
    };
  });
</script>

<style>
  main {
    height: 100%;
    width: 100%;
    padding: 1em;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: center;

    font-family: "Iosevka Curly Slab", monospace;
  }
</style>

<main>
  <h1>{timeString}</h1>
</main>
