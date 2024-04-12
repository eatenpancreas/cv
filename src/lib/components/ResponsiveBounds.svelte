<script lang="ts">
  import {twMerge} from "tailwind-merge";

  let className = "";
  export { className as class }
</script>

<div 
  class={twMerge(
    "min-h-[100vh] w-screen max-w-4xl px-4 sm:px-10 flex flex-col items-center justify-center"
    , className
  )}
><slot/></div>