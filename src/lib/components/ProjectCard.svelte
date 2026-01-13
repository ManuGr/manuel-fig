<script lang="ts">
    export let src;
    export let title;
    export let description;
    export let stack: string[];
</script>

<a href="https://github.com/ManuGr?tab=repositories" target="_blank" class="w-full group dark:border dark:border-[#666] rounded-xl flex flex-col justify-between dark:shadow-sm dark:shadow-[#666] hover:scale-101 hover:-translate-y-1 transition-transform duration-300">
    <div class="w-full h-full flex flex-col gap-2">
        <div class="w-full h-1/2 bg-amber-500 relative rounded-t-xl flex items-end justify-center">
            <div class="absolute w-11/12 h-11/12 bg-black/50 blur-xl transition-all duration-200"></div>
            <img {src} alt="thumbnail" class="w-5/6 h-5/6 z-10 object-cover object-top rounded-t-xl group-hover:scale-105 group-hover:-translate-y-1.5 transition-all duration-300">
        </div>
        <div class="w-full flex flex-col gap-2 px-4 py-2">
            <h2 class="text-xl font-semibold">{title}</h2>
            <p>{description}</p>
            <div class="flex gap-2">
                {#each stack as tech}
                    <p class="bg-black/20 dark:bg-white/5 px-2 py-1 rounded-full text-sm">{tech}</p>
                {/each}
            </div>
        </div>
    </div>
    <p class="p-4 flex items-center gap-2 text-lg">View repo <span class="icon-[mdi--arrow-right] group-hover:translate-x-1.5 transition-transform duration-200"></span></p>
</a>