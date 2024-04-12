<script lang="ts">
  import NavLink from "$lib/components/NavLink.svelte";
  export let title: string;
  export let links: { name: string; href: string }[];
  
  let open = false;
</script>

<div class={"fixed z-40 lg:h-10 overflow-clip transition-all " + (open ? "h-40" : "h-16")}>
  <div class="bg-gradient-to-br from-gray-900 to-yellow-950 h-screen w-screen"></div>
</div>

<div class="text-white flex w-full justify-center gap-4 items-center uppercase lg:flex-row flex-col px-4 py-2 fixed z-50">
  <div class={"overflow-scroll -mt-3 transition-all flex flex-col items-center " + (open ? "h-20": "h-0")}>
    {#each links as {href, name}, i}
      <NavLink
        onClick={() => open = false}
        {href}
      >
        {name}
      </NavLink>
    {/each}
  </div>
  
  <div class={"lg:hidden border-white hover:border-yellow-200 transition-all " + (open ? "": "-mt-2")}
       on:click={() => open = !open}>
    
    <div class="border-inherit border-b w-20 mb-0.5"></div>
    <div class="border-inherit border-b w-20 mb-0.5"></div>
    <div class="border-inherit border-b w-20 mb-0.5"></div>
  </div>

  {#each links as {href, name}, i}
    <NavLink 
     onClick={() => open = false} 
     class={(i >= links.length / 2 ? "order-1 ": "") + "invisible lg:visible"} 
     {href}
    >
      {name}
    </NavLink>
  {/each}
  <div class="-order-1 lg:order-none opacity-60">{title}</div>
</div>