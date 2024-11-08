<script>
    export let text = "Click me";
    
    // ASCII chars for border
    const chars = {
      topLeft: "+",
      topRight: "+",
      bottomLeft: "+",
      bottomRight: "+",
      vertical: "|", 
      horizontal: "-"
    };
  
    $: width = text.length;
    $: horizontalLine = chars.horizontal.repeat(width + 2);
    $: paddedText = ` ${text} `;
</script>
  
<button 
  class="ascii-button"
  on:click
>
  <div class="button-content" role="presentation">
    <div class="line">
      <span class="corner">{chars.topLeft}</span>
      <span class="horizontal">{horizontalLine}</span>
      <span class="corner">{chars.topRight}</span>
    </div>
    <div class="line">
      <span class="corner">{chars.vertical}</span>
      <span class="text">{paddedText}</span>
      <span class="corner">{chars.vertical}</span>
    </div>
    <div class="line">
      <span class="corner">{chars.bottomLeft}</span>
      <span class="horizontal">{horizontalLine}</span>
      <span class="corner">{chars.bottomRight}</span>
    </div>
  </div>
</button>
  
<style>
  .ascii-button {
    background: none;
    border: none;
    padding: 0;
    margin: 0;
    cursor: pointer;
    color: inherit;
    /* Use a simpler monospace font stack */
    font-family: Consolas, "Courier New", monospace;
    user-select: none;
    -webkit-user-select: none;
    display: inline-block;
  }
  
  .button-content {
    display: inline-block;
    line-height: 1;
  }

  .line {
    height: 1.2em;
    white-space: pre;
    display: flex;
    line-height: 1;
  }

  .horizontal {
    white-space: pre;
  }

  .text {
    display: inline-block;
  }

  .corner {
    display: inline-block;
    line-height: 1;
  }
  
  .ascii-button:hover {
    opacity: 0.8;
  }
  
  .ascii-button:focus {
    outline: 2px solid #666;
    outline-offset: 2px;
  }
  
  .ascii-button:active {
    transform: translateY(1px);
  }
</style>