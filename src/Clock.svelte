<script lang="ts">
  import { onMount } from "svelte";

  let time = new Date();

  $: hours = time.getHours();
  $: minutes = time.getMinutes();
  $: seconds = time.getSeconds();
  $: weekday = time.toLocaleDateString("en-US", { weekday: "long" });

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
  section {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .separator {
    opacity: 0.6;
  }

  #time {
    display: flex;
    font-size: 2.5em;
    align-items: center;
    margin-bottom: 10px;
  }
  #time .meridiem {
    margin-left: 20px;
    font-size: 0.6em;
    opacity: 0.8;
  }

  #weekday {
    font-size: 1em;
    margin-bottom: 15px;
    opacity: 0.8;
  }

  #year {
    display: flex;
    font-size: 1.5em;
  }
</style>

<section>
  <div id="time">
    <span>{String(hours % 12).padStart(2, '0')}</span>
    <span class="separator">:</span>
    <span>{String(minutes).padStart(2, '0')}</span>
    <span class="separator">:</span>
    <span>{String(seconds).padStart(2, '0')}</span>
    <span class="meridiem">{hours >= 12 ? 'p.m.' : 'a.m.'}</span>
  </div>
  <p id="weekday">{weekday}</p>
  <p id="year">
    <span>{time.getUTCFullYear()}</span>
    <span class="separator">-</span>
    <span>{time.getUTCMonth() + 1}</span>
    <span class="separator">-</span>
    <span>{time.getUTCDate()}</span>
  </p>
</section>
