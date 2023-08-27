# svelte-simple-feather

svelte-simple-feather is lightweight simple feather icons library for svelte.

## Installation

### npm
```bash
npm i svelte-simple-feather
```

## Usage

Just import `Icon` component from `svelte-simple-feather` and use it with `icon` prop for the icon name. You can find all the available icons [here](https://feathericons.com/).

```sveltehtml

### Basic
```sveltehtml
<script>
  import { Icon } from 'svelte-simple-feather'
</script>

<Icon icon="activity" />
```

### Custom size & color
```sveltehtml
<script>
  import { Icon } from 'svelte-simple-feather'
</script>

<div style="color: #ededed; font-size: 2rem">
 <Icon icon="activity" />
</div>
```

## License

Licensed under the MIT License. 

