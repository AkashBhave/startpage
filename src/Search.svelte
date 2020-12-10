<script lang="ts">
  import { onMount } from "svelte";

  $: bang = "g"; // Default to Google search
  let bangInput;
  $: search = "";
  let searchInput;

  onMount(() => searchInput.focus());

  const handleKeyup = (event: KeyboardEvent) => {
    // Focus on bang if "!" is entered
    if (search.startsWith("!") || bang.includes("!")) {
      search = "";
      bang = "";
      bangInput.focus();
      return;
    }
    // Check that bang is filled on tab
    if (event.code == "Tab") {
      if (bang == "") bang = "g";
      return;
    }
    // Submit the search with DuckDuckGo
    if (event.code == "Enter") {
      if (bang == "") bang = "g";
      const url = `https://duckduckgo.com/?q=!${encodeURIComponent(bang)} ${encodeURIComponent(search)}`;
      console.log(url);
      window.location.replace(url);
      return;
    }
  };
</script>

<style>
  section {
    display: flex;
    width: 50%;
    align-items: center;
    justify-items: center;
  }

  input {
    display: block;
    font-weight: 500;
    font-family: inherit;
    font-size: 0.6em;
    -webkit-appearance: none;
    transition: border 0.3s ease;
    height: 50px;
    padding: 0 20px;
  }
  input:focus {
    outline: none;
    border-color: red;
  }
  #exclamation,
  #bang {
    background-color: #183675;
    color: #f7f5f5;
    border: 2px solid gainsboro;
    flex-grow: 0;
    display: block;
    opacity: 0.8;
    font-size: 0.5em;
    font-weight: bold;
  }
  #bang {
    width: 100px;
  }
  #exclamation {
    height: 50px;
    padding: 0 20px;
    display: flex;
    align-items: center;
  }
  #search {
    border-radius: 5px;
    border-top-left-radius: 0px;
    border-bottom-left-radius: 0px;
    width: fit-content;
    color: #183675;
    background: #f7f5f5;
    border: 2px solid gainsboro;
    flex-grow: 1;
  }
</style>

<section>
  <p id="exclamation">!</p>
  <input
    bind:this={bangInput}
    type="text"
    id="bang"
    bind:value={bang}
    on:keyup|preventDefault={handleKeyup} />
  <input
    bind:this={searchInput}
    type="text"
    id="search"
    bind:value={search}
    on:keyup|preventDefault={handleKeyup} />
</section>
