<script lang="ts">
    import resume from "$lib/assets/Manuel Figueiredo Resume.pdf"
</script>

<div class="w-full flex justify-between items-center border-t border-gray-400 pt-2">
    <div>
        <h1 class="text-xl font-semibold">Interested in working with me?</h1>
        <p>Download my resume for more information on my working experience</p>
    </div>
    <a download="Manuel Figueiredo Resume.pdf" target="_blank" href={resume} class="flex items-center gap-2 px-6 py-2 font-medium rounded-lg border cursor-pointer hover:scale-105 transition-transform duration-200">
        Resume
        <span class="icon-[material-symbols--download] text-xl"></span>
    </a>
</div>