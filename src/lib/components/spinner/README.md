# ASCII Spinner Component

A flexible ASCII-based loading spinner with various positioning and alignment options.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| speed | number | 100 | Animation speed in milliseconds |
| size | string\|number | 'md' | Size of spinner ('sm', 'md', 'lg', 'xl' or number) |
| align | string | 'inline' | Alignment ('inline', 'left', 'center', 'right') |
| position | string | 'static' | Position ('static', 'absolute', 'fixed') |
| overlay | boolean | false | Whether to show spinner in a full-screen overlay |

## Size Options
- `sm`: 1em
- `md`: 1.5em
- `lg`: 2em
- `xl`: 3em
- Custom: Any number (in em units)

## Alignment Options
- `inline`: Displays inline with text
- `left`: Left-aligned block
- `center`: Center-aligned block
- `right`: Right-aligned block

## Position Options
- `static`: Normal flow (default)
- `absolute`: Centered in nearest positioned ancestor
- `fixed`: Centered in viewport

## Examples

```svelte
<!-- Basic inline usage -->
<div>Loading <Spinner /></div>

<!-- Centered in container -->
<div style="position: relative; height: 200px;">
  <Spinner size="lg" align="center" />
</div>

<!-- Fixed position overlay -->
<Spinner overlay size="xl" />

<!-- Right-aligned -->
<Spinner align="right" size="lg" />

<!-- Absolute positioned in a container -->
<div style="position: relative; height: 300px;">
  <Spinner position="absolute" size="xl" />
</div>

<!-- Common loading states -->

<!-- Button loading -->
<button disabled>
  <Spinner size="sm" /> Loading...
</button>

<!-- Card loading -->
<div class="card">
  <Spinner align="center" size="lg" />
</div>

<!-- Full page loading -->
<Spinner overlay size="xl" />

<!-- Custom placement -->
<div style="position: relative;">
  <Spinner 
    position="absolute" 
    size="lg"
    style="top: 1rem; right: 1rem;"
  />
</div>
```

## Styling

The spinner uses em units and is fully responsive. When using the overlay option, it creates a semi-transparent white background that can be customized via CSS.

## Accessibility

The spinner includes appropriate ARIA labels and can be made more accessible by adding additional context:

```svelte
<div aria-live="polite" role="status">
  <Spinner /> Loading content...
</div>
```