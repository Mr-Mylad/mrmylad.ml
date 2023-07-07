<script>
    import { page } from "$app/stores";
</script>

<svelte:head>
    <title>Error {$page.status}</title>
</svelte:head>

<div id="errorMessage">
    {#if $page.status === 404}
        <div class="flex items-center justify-center">
            <img class="rounded-3xl dark:border-4 dark:border-white" src="https://tenor.com/en-GB/view/not-found-404error-crash-glitch-gif-23664505.gif" alt="404 error">
        </div>
    {:else}
        <h1 class="text-center text-3xl text-black dark:text-white">Sorry! 🥲</h1>
    {/if}
    <br>
    <h3 class="text-center text-xl font-bold text-black dark:text-white">There was an error in loading this page...</h3>
    <h5 class="text-center text-lg font-bold text-black dark:text-white">Error:</h5>
    <h1 class="text-center text-3xl text-red-700 dark:text-red-700">{$page.status}: {$page.error?.message}</h1>
</div>