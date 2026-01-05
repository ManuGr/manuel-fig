<script lang="ts">
    import { browser } from "$app/environment";
	import { onMount } from "svelte";
    
    let darkMode = true;
    let altHeader = false;
    
    const changePx = 100;
    
    const links = [
        {id: 'home', label: 'Home'},
        {id: 'about', label: 'About me'},
        {id: 'projects', label: 'Project'},
        {id: 'resume', label: 'Resume'},
        {id: 'contact', label: 'Contact me'}
    ];

    const buttons = [
        {url: 'https://github.com/ManuGr', icon: 'icon-[line-md--github]', label: 'github link'},
        {url: 'https://www.linkedin.com/in/manuel-grgic/', icon:'icon-[mdi--linkedin]', label: 'linkedin link'}
    ];

    function handleScroll() {
        altHeader = document.documentElement.scrollTop > changePx;
    }

    function handleSwitch() {
        console.log(altHeader);
        darkMode = !darkMode;

        localStorage.setItem('theme', darkMode ? 'dark' : 'light');

        darkMode
            ? document.documentElement.classList.add('dark')
            : document.documentElement.classList.remove('dark');
    }

    let target = null;

    if (browser) {
        if (localStorage.theme === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
            document.documentElement.classList.add('dark');
            darkMode = true;
        } else {
            document.documentElement.classList.remove('dark');
            darkMode = false;
        }
    }

    onMount(() => {

        function handleIntersection(entries: any) {
            entries.map((entry: any) => {
                if(entry.isIntersecting) {
                    document.querySelector(`#${entry.target.id}-link`)?.classList.add('dark:text-[#ccc]', 'text-[#555]', 'border-b-2', 'border-[#555]', 'dark:border-[#ccc]');
                } else {
                    document.querySelector(`#${entry.target.id}-link`)?.classList.remove('dark:text-[#ccc]', 'text-[#555]', 'border-b-2', 'border-[#555]', 'dark:border-[#ccc]');
                }
            });
        }

        const options = {
            threshold: 0.55
        }

        const observer = new IntersectionObserver(handleIntersection, options);

        document.querySelectorAll('#home, #about, #projects, #resume, #contact').forEach((el) => {
            if(el) {
                observer.observe(el);
            }
        });
    });
</script>

<svelte:window on:scroll={handleScroll} />

<header class="fixed w-full flex justify-center">
    <div class="{altHeader ? 'w-2/3 rounded-full mt-4' : 'w-full'} flex items-center justify-between p-4 {darkMode ? 'bg-white/5' : 'bg-black/12'} backdrop-blur-xl transition-all duration-300 ease-in-out">
        <ul class="flex items-center gap-2">
            {#each links as link}
                <li>
                    <a
                        id="{link.id}-link"
                        href="#{link.id}"
                        class="px-3 py-1.5 dark:hover:text-[#ccc] hover:text-[#555] transition-colors duration-200 w-11/12"
                    >
                        {link.label}
                    </a>
                </li>
            {/each}
        </ul>
        <ul class="flex items-center gap-2">
            <li>
                <button class="p-2 flex items-center justify-center rounded-full {darkMode ? 'bg-white/25' : 'bg-black/15'} text-xl hover:scale-110 transition-all duration-300 ease-in-out" on:click={handleSwitch}>
                    <span class="icon-[material-symbols--{darkMode ? 'dark' : 'light'}-mode-outline-rounded]">toggle mode</span>
                </button>
            </li>
            {#each buttons as btn}
                <li>
                    <a href={btn.url} class="p-2 flex items-center justify-center rounded-full {darkMode ? 'bg-white/25' : 'bg-black/15'} text-xl hover:scale-110 transition-all duration-300 ease-in-out">
                        <span class={btn.icon}>{btn.label}</span>
                    </a>
                </li>
            {/each}
        </ul>
    </div>
</header>