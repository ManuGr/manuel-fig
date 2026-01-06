<script lang="ts">
    import manuel from "$lib/assets/manuel.jpg";
    import franuel_hm from "$lib/assets/franuel_hm.jpeg";
    import cats from "$lib/assets/gatinos.jpeg";
	import { onMount } from "svelte";

    let secondary_img = manuel;
    let hover = false;

    function onMouseEnter(src: any) {
        secondary_img = src;
        hover = true;
    }

    onMount(() => {
        const target = document.querySelector("#about > div");

        function handleIntersection(entries: any) {
            entries.map((entry: any) => {
                if(entry.isIntersecting) {
                    entry.target.classList.remove("opacity-0", "-translate-y-full");
                    entry.target.classList.add("opacity-100", "translate-y-0");
                } else {
                    entry.target.classList.add("opacity-0", "-translate-y-full");
                    entry.target.classList.remove("opacity-100", "translate-y-0");
                }
            });
        }

        const observer = new IntersectionObserver(handleIntersection);

        observer.observe(target);
    })

</script>

<div id="about" class="w-full h-dvh flex flex-col items-center justify-center gap-20 lg:pt-24 overflow-hidden">
    <div class="w-5/6 h-5/6 px-6 py-4 flex justify-around gap-40 rounded-lg opacity-0 -translate-y-full transition-all duration-1000 ease-in-out delay-200">
        <div class="w-full h-full flex flex-col gap-6 pt-12">
            <div class="flex flex-col gap-1">
                <h1 class="text-xl md:text-4xl font-semibold">Manuel Figueiredo</h1>
                <h2 class="md:text-xl font-medium">Software Engineer</h2>
            </div>
            <p class="md:text-xl relative group text-justify">
                I am a Software Engineer with an interest in Frontend Web Development, holding a Bachelor's Degree in Computer Science. I have worked in both established and newly created
                companies in Switzerland, and through these experiences I've had the opportunity to hone my skills in web development, software design and engineering, and IT support. I am
                independent and a quick learner who thrives on tackling new challenges and figuring things out. However, I feel like I grow the most when I get to bring my upbeat
                personality into a collaborative environment.
                <br>
                <br>
                I am
                <span
                    on:mouseenter={ () => onMouseEnter(franuel_hm) }
                    on:mouseleave={ () => hover = false }
                    class="xl:underline xl:cursor-pointer"
                    role="none"
                >married to a wonderful and creative person</span>
                who constantly inspires me. Together, we have
                <span
                    on:mouseenter={ () => onMouseEnter(cats) }
                    on:mouseleave={ () => hover = false }
                    class="xl:underline xl:cursor-pointer"
                    role="none"
                >two adorable cats (August and Ivy)</span>
                . Outside of that, I love delving into the stories and worlds brought about by video games, especially turn-based RPGs.
                My wife and I also love collecting physical media, CDs tend to be my domain while my wife likes to focus on her collection of vynils. And at the
                end of the day, I like to wind down with a good book, whether it's fiction or non-fiction. 
            </p>
        </div>
        <div class="hidden xl:block relative w-2/5 h-full group overflow-hidden">
            <img
                src={manuel}
                alt="Manuel Figueiredo"
                class="w-full h-full object-cover object-top {hover ? 'opacity-0 translate-x-full' : 'translate-x-0'} absolute transition-all duration-500"
            >
            <img
                src={secondary_img}
                alt="Manuel and wife"
                class="w-full h-full object-cover {hover ? 'translate-x-0 opacity-100' : 'translate-x-full opacity-0'} absolute transition-all duration-500"
            >
        </div>
    </div>
</div>