<script lang="ts">
  let hours = new Date().getHours();
</script>

<style>
  section {
    display: flex;
  }

  #name {
    opacity: 0.8;
  }
</style>

<section>
  <p>
    {#if 6 <= hours && hours <= 12}
      <span>Good morning</span>
    {:else if 13 <= hours && hours <= 16}
      <span>Good afternoon</span>
    {:else if 17 <= hours && hours <= 22}
      <span>Good evening</span>
    {:else}<span>Go to sleep</span>{/if}
  </p>
  <p id="name">, Akash.</p>
</section>
