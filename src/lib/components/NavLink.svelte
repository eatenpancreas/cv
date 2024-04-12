<script>
  import {twMerge} from "tailwind-merge";

  export let href = '';
  let className = '';
  export {className as class};
  export let onClick = () => {};
</script>

<a {href} on:click={onClick}
  class={twMerge("flex items-center gap-1 text-sm hover:text-yellow-200 hover:border-yellow-200 border-white transition-colors", className)}>
  <div class="border-b-4 border-inherit w-8"></div>
  <div><slot/></div>
  <div class="border-b-4 border-inherit w-8"></div>
</a>