<script lang="ts">
    import "$lib/index.css";
    let app: HTMLDivElement;
    let darkModeEnabled: boolean = false;
    const toggleDarkMode: () => void = () => {
        darkModeEnabled = !darkModeEnabled;
    };
    $: appDivClass = `${darkModeEnabled ? "dark bg-gray-800" : "bg-gray-50"}`;
</script>

<div id="app" class={appDivClass} bind:this={app}>
    <nav class="mb-1 text-right w-screen text-black dark:text-white bg-white dark:bg-gray-950">
        <button class="border border-gray-950" on:click={toggleDarkMode}>{darkModeEnabled ? "Light Mode" : "Dark Mode"}</button>
    </nav>
    <slot />
</div>