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
  @font-face {
    font-family: "Iosevka Curly Slab";
    src: url("/fonts/iosevka-curly-slab-regular.woff2") format("woff2"),
      url("/fonts/iosevka-curly-slab-regular.woff") format("woff");
    font-weight: normal;
  }
  @font-face {
    font-family: "Iosevka Curly Slab";
    src: url("/fonts/iosevka-curly-slab-semibold.woff2") format("woff2"),
      url("/fonts/iosevka-curly-slab-semibold.woff") format("woff");
    font-weight: bold;
  }

  main {
    height: 100%;
    width: 100%;
    padding: 1em;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: center;

    font-family: "Iosevka Curly Slab", monospace;
    font-size: 2em;
    font-weight: normal;

    background-color: #dee5f0;
    color: #183675;
  }
</style>

<main>
  <p>{timeString}</p>
</main>
