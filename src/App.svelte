<style>
  .time {
    font-weight: bold;
  }
</style>

<script>
  import { onMount } from 'svelte';

  export let name = 'Anonymous';
  let time = new Date();

  onMount(() => {
    const timer = setInterval(() => {
      time = new Date();
    }, 1000);

    return () => {
      clearInterval(timer);
    }
  })

  let hours, minutes, seconds;

  $: {
    hours = time.getHours();
    minutes = time.getMinutes();
    seconds = time.getSeconds();
  }
</script>

<p>
  Hello {name}, the time is <span class="time">{hours}:{minutes}:{seconds}</span>
</p>

