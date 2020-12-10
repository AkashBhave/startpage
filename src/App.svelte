<script lang="ts">
  import Clock from "./Clock.svelte";
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
    margin: 0 auto;
    display: flex;
    flex-direction: column;
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
  <Clock />
</main>
