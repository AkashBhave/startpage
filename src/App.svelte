<script lang="ts">
  import Clock from "./Clock.svelte";
  import Greeting from "./Greeting.svelte";
  import Links from "./Links.svelte";
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
  @media screen and (max-height: 650px) {
    main {
      font-size: 3.5vh;
    }
  }

  hr {
    width: 30%;
    opacity: 0.2;
    margin: 30px auto;
  }
</style>

<main>
  <Greeting />
  <hr />
  <Clock />
  <hr />
  <Links />
</main>
