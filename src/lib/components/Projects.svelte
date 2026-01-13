<script lang="ts">
    import portfolio from "$lib/assets/portfolio.png";
	import ProjectCard from "./ProjectCard.svelte";

    let description = "A simple website where I get to showcase who I am and what I've done."
    let stack = ["Svelte", "TailwindCSS", "HTML", "CSS", "TypeScript"]
</script>

<div id="projects" class="w-full h-dvh flex items-center justify-center">
    <div class="w-11/12 lg:w-3/5 h-2/3 flex flex-col items-center justify-start gap-4">
        <div class="w-full flex justify-between items-center">
            <h1 class="text-2xl font-semibold">My Projects</h1>
            <a href="https://github.com/ManuGr?tab=repositories" target="_blank" class="group flex gap-2 items-center border border-[#666] bg-black/5 dark:bg-black/20 hover:bg-black/7 dark:hover:bg-black/10 px-4 py-2 rounded-lg">
                <span class="icon-[line-md--github]"></span>
                <p>View all repos</p>
                <span class="icon-[quill--link-out]"></span>
            </a>
        </div>
        <div class="w-full h-full flex flex-col gap-4 lg:grid lg:grid-cols-2">
            <ProjectCard src={portfolio} title="Personal website" {description} {stack} />
        </div>
    </div>
</div>