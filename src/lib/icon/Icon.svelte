<script>
    /**
     * @type {string}
     * @default ''
     * @description The name of the icon to display.
     */
    export let icon = '';
</script>

<svg class="icon" viewBox="0 0 24 24">
    <use href="/assets/feather.sprite.svg#{icon}"></use>
</svg>

<style>
    .icon {
        width: 1em;
        height: 1em;
        fill: currentColor;
    }
</style>