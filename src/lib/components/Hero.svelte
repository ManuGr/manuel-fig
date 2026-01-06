<script lang="ts">
	import { goto } from "$app/navigation";

    
</script>

<div id="home" class="w-full h-dvh flex flex-col items-center justify-center gap-20 lg:pt-24">
    <div class="flex flex-col items-center justify-center gap-4">
        <h2 class="text-3xl md:text-7xl font-medium">Hello, I'm Manuel</h2>
        <p class="text-xl md:text-5xl">An experienced Software Engineer</p>
    </div>

    <button class="relative group border-0 px-2 py-1 h-10 text-sm md:text-xl font-medium w-1/4 md:w-1/12 flex items-center justify-center cursor-pointer hover:bg-amber-600 hover:scale-110 hover:-translate-y-1 hover:text-white transition-all duration-200" on:click={() => goto('#about')}>
        <span class="group-hover:w-full group-hover:border-amber-600 w-1/6 h-full left-0 absolute border-l border-y border-black dark:border-white transition-all duration-200"></span>
        <p class="absolute">Learn More</p>
        <span class="group-hover:w-full group-hover:border-amber-600 w-1/6 h-full right-0 absolute border-r border-y border-black dark:border-white transition-all duration-200"></span>
    </button>
</div>