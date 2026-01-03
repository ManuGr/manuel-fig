<script lang="ts">
    import { browser } from "$app/environment";

    import NavButtons from "./NavButtons.svelte";
    
    let darkMode = true;
    let altHeader = false;
    
    const changePx = 100;
    const links = [
        {id: 'about', label: 'About me'},
        {id: 'projects', label: 'Project'},
        {id: 'resume', label: 'Resume'},
        {id: 'contact', label: 'Contact me'}
    ]

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

    if (browser) {
        if (localStorage.theme === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
            document.documentElement.classList.add('dark');
            darkMode = true;
        } else {
            document.documentElement.classList.remove('dark');
            darkMode = false;
        }
    }
</script>

<svelte:window on:scroll={handleScroll} />

<header class="fixed w-full flex justify-center">
    <div class="fixed {altHeader ? 'w-2/3 rounded-full mt-4' : 'w-full'} flex items-center justify-between p-4 {darkMode ? 'bg-white/5' : 'bg-black/12'} backdrop-blur-xl transition-all duration-300 ease-in-out">
        <div>
            <h1 class="text-xl font-semibold">Manuel Figueiredo</h1>
        </div>
        <ul class="flex items-center gap-2">
            <li>
                <button class="p-2 flex items-center justify-center rounded-full {darkMode ? 'bg-white/25' : 'bg-black/15'} transition-colors duration-200 ease-in-out" on:click={handleSwitch}>
                    <span class="material-symbols-outlined">
                        {darkMode ? 'dark_mode' : 'light_mode'}
                    </span>
                </button>
            </li>
            {#each links as link}
                <li>
                    <NavButtons id={link.id} label={link.label} />
                </li>
            {/each}
        </ul>
    </div>
</header>