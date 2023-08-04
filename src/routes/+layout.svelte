<script lang="ts">
    import "$lib/index.css";
    import { onMount } from "svelte";

    let darkModeEnabled: boolean = true;

    onMount(() => {
        darkModeEnabled = localStorage.darkModeEnabled ? 
            localStorage.darkModeEnabled === "true" ? true : false 
        : true;
    });

    const toggleDarkMode: () => void = () => {
        darkModeEnabled = !darkModeEnabled;
        localStorage.darkModeEnabled = darkModeEnabled;
    }
    $: appDivClass = `${darkModeEnabled ? "dark bg-gray-950" : "bg-slate-50"} h-screen m-0`;
</script>

<div id="app" class={appDivClass}>
    <!-- Sidebar -->
    <nav class="fixed bottom-0 right-0 h-16 w-full sm:w-16 m-0 flex text-black dark:text-white bg-slate-300 dark:bg-gray-800 shadow-lg sm:flex-col sm:justify-center sm:items-center sm:h-screen">
        <button class="sidebar-icon" on:click={toggleDarkMode}>{darkModeEnabled ? "Light Mode" : "Dark Mode"}</button>
        <hr class="h-fit mb-2 border-gray-800 dark:border-slate-300 border-y sm:hidden" />
        <button class="sidebar-icon" on:click={() => open("/", "_self")}>Home</button>
        <button class="sidebar-icon" on:click={() => open("/AboutMe/", "_self")}>About Me</button>
    </nav>
    <slot />
</div>