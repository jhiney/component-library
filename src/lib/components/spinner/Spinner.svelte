<script>
    export let speed = 100;
    
    const frames = ['|', '/', '-', '\\'];
    let currentFrameIndex = 0;
    let intervalId;
    
    import { onMount, onDestroy } from 'svelte';
    
    onMount(() => {
      intervalId = setInterval(() => {
        currentFrameIndex = (currentFrameIndex + 1) % frames.length;
      }, speed);
    });
    
    onDestroy(() => {
      if (intervalId) clearInterval(intervalId);
    });
</script>
  
<span class="spinner" aria-label="Loading">
    {frames[currentFrameIndex]}
</span>
  
<style>
    .spinner {
      font-family: Consolas, "Courier New", monospace;
      display: inline-block;
      user-select: none;
      -webkit-user-select: none;
    }
</style>