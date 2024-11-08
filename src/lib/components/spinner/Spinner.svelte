<script>
    export let speed = 100;
    export let size = 'md';
    export let align = 'inline'; // inline, left, center, right
    export let position = 'static'; // static, absolute, fixed
    export let overlay = false; // Creates full-screen overlay when true
    
    const frames = ['|', '/', '-', '\\'];
    let currentFrameIndex = 0;
    let intervalId;
    
    //in Em units
    const sizes = {
      sm: '1',
      md: '1.5',
      lg: '2',
      xl: '3'
    };
    
    $: fontSize = sizes[size] || size;
    
    //  classes based on props
    $: classes = [
      'spinner',
      `align-${align}`,
      position !== 'static' ? `position-${position}` : '',
      overlay ? 'overlay' : ''
    ].filter(Boolean).join(' ');
    
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
  
  {#if overlay}
    <div class="overlay-container">
      <span 
        class={classes}
        aria-label="Loading"
        style="font-size: {fontSize}em;"
      >
        {frames[currentFrameIndex]}
      </span>
    </div>
  {:else}
    <span 
      class={classes}
      aria-label="Loading"
      style="font-size: {fontSize}em;"
    >
      {frames[currentFrameIndex]}
    </span>
  {/if}
  
  <style>
    .spinner {
      font-family: Consolas, "Courier New", monospace;
      display: inline-block;
      user-select: none;
      -webkit-user-select: none;
      line-height: 1;
      width: 1em;
      height: 1em;
      text-align: center;
    }
  
    /* Alignment utilities */
    .align-left {
      display: block;
      text-align: left;
    }
  
    .align-center {
      display: block;
      text-align: center;
    }
  
    .align-right {
      display: block;
      text-align: right;
    }
  
    .align-inline {
      display: inline-block;
      vertical-align: middle;
    }
  
    /* Position utilities */
    .position-absolute {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
  
    .position-fixed {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      z-index: 1000;
    }
  
    /* Overlay styles */
    .overlay-container {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(255, 255, 255, 0.9);
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 1000;
    }
  
    .overlay {
      display: block;
    }
  
    /* Optional: Add animation for overlay appearance */
    .overlay-container {
      animation: fadeIn 0.2s ease-in-out;
    }
  
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }
  </style>