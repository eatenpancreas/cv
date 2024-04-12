<script lang="ts">
    import TypingTitle from "$lib/components/TypingTitle.svelte";
    import {onMount} from "svelte";
    import RegionHover from "$lib/components/RegionHover.svelte";
    import ResponsiveBounds from "$lib/components/ResponsiveBounds.svelte";
    import * as Carousel from "$lib/components/ui/carousel";
    
    let beginWriting: (title: string, idx: number, then: (idx: number) => void) => void;
    let deleteCharacters: (amount: number, then: (idx: number) => void) => void;
    let active: boolean = true;
    
    onMount(() => 
      beginWriting("Hello World!", 0, () => 
        beginWriting("I am Pascal d'Achard van Enscrut", 0, () =>
          deleteCharacters(2, (i) =>
            beginWriting("I am Pascal d'Achard van Enschut", i, () => { active = false })
          )
        )
      )
    )
</script>

<!--<div class="snap-y snap-proximity w-full h-screen overflow-y-scroll">-->

<ResponsiveBounds>
    <h1 class="text-2xl font-mono">
        <TypingTitle
            bind:beginWriting={beginWriting}
            bind:deleteCharacters={deleteCharacters}
            {active}
        />
    </h1>
    <RegionHover right={80} left={80} top={20} bottom={20}>
        <div class="select-none" style="transform: scale(5, 1)">v</div>
    </RegionHover>
    <img src="pascal_foto.jpg" alt="Pascal" class="mt-10 rounded-full shadow-2xl aspect-square object-cover w-40"/>
</ResponsiveBounds>

<div class="bg-white/10 w-full">
    <ResponsiveBounds class="flex-row">
        <h2 class="text-4xl w-72 font-mono">Check out some of my projects</h2>

        <Carousel.Root class="ml-14">
            <Carousel.Content>
                <Carousel.Item>...</Carousel.Item>
                <Carousel.Item>...</Carousel.Item>
                <Carousel.Item>...</Carousel.Item>
            </Carousel.Content>
            <Carousel.Previous class="bg-transparent"/>
            <Carousel.Next class="bg-transparent"/>
        </Carousel.Root>
    </ResponsiveBounds>
</div>

<ResponsiveBounds>
</ResponsiveBounds>