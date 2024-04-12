<script lang="ts">
    export let left = 2.5;
    export let top = 2.5;
    export let right = 2.5;
    export let bottom = 2.5;
    export let onmouseleave = () => {};
    export let onmouseenter = () => {};
    export let onmousemove = () => {};
    export let onmousedown = () => {};
    export let onmouseup = () => {};
    export let onclick = () => {};
</script>

<div class="relative">
    <div class="absolute" 
         style="left: -{left}rem; right: -{right}rem;
                top: -{top}rem; bottom: -{bottom}rem;"
        on:mouseleave={onmouseleave}
        on:mouseenter={onmouseenter}
        on:mousemove={onmousemove}
        on:mousedown={onmousedown}
        on:mouseup={onmouseup}
        on:click={onclick}
    ></div>
    <slot/>
</div>