<script>
    const showOnPx = 250;
    let showBtn = false;

    function handleScroll() {
        showBtn = document.documentElement.scrollTop > showOnPx;
    }
</script>

<svelte:window on:scroll={handleScroll} />

<div id="home" class="h-dvh pt-20">
    <h1>Manuel Figueiredo</h1>
</div>
<div id="about" class="h-dvh pt-20">
    <h1>About me</h1>
</div>
<div id="projects" class="h-dvh pt-20">
    <h1>Projects</h1>
</div>
<div id="resume" class="h-dvh pt-20">
    <h1>Resume</h1>
</div>
<div id="contact" class="h-dvh pt-20">
    <h1>Contact me</h1>
</div>

<a
    href="#home"
    class="{showBtn ? '' : 'opacity-0'} fixed bottom-10 right-10 flex items-center justify-center p-2 hover:scale-115 transition-all duration-500 ease-in-out rounded-full dark:bg-black/15 bg-white/10"
>
    <span class="material-symbols-outlined">arrow_upward</span>
</a>