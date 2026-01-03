<script lang="ts">
    interface Props {
        id: string;
        label: string;
    }

    const {id, label}: Props = $props();

    function scrollIntoView() {

    }
</script>

<a
    href="#{id}"
    class="px-3 py-1.5 rounded-lg dark:hover:bg-white/10 hover:bg-black/10 transition-colors duration-200"
>
    {label}
</a>