<script>
    import "../app.css";
    import Navigation from "$lib/components/Navigation.svelte";
</script>

<div class="bg-gradient-to-br from-gray-900 to-yellow-950 h-screen fixed w-screen -z-50"></div>

<Navigation title="Pascal d'Achard van Enschut" links={[
  { name: "Home", href: "/" },
  { name: "Blog", href: "/blog" },
  { name: "Projects", href: "/projects" },
  { name: "Contact", href: "/contact" },
]}/>

<div class="flex flex-col min-h-screen justify-center items-center text-white max-w-full overflow-clip">
    <slot/>
</div>