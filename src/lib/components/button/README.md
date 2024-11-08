# ASCII Button Component

A retro-styled ASCII button component that creates a text-based button with box-drawing characters.

## Usage

```svelte
<script>
  import { Button } from '$lib/components/button';
</script>

<Button 
  text="Click me!"
  on:click={() => console.log('Clicked!')}
/>
```

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| text | string | "Click me" | The text to display inside the button |

## Events

The component forwards the native button click event.

## Examples

```svelte
<!-- Basic usage -->
<Button text="Submit" />

<!-- With click handler -->
<Button 
  text="Delete"
  on:click={() => handleDelete()}
/>

<!-- Long text automatically adjusts width -->
<Button text="This is a longer button text" />
```

## Styling

The size automatically adjusts based on the text content.

Default appearance:
```
+----------+
| Click me |
+----------+
```