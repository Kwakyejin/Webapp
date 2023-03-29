<script>
    export let data;
    import {Spinner} from 'flowbite-svelte'
    import {onMount} from 'svelte'
    import {get} from '$lib/utils.js'
    import {Heading, P, A} from 'flowbite-svelte'

    let result;

    async function getResult(){
        result = await get(`/result?task_id=${data.task_id}`)
        if (result.status == "running"){
            setTimeout(getResult, 1000)
        }
    }

    onMount(async () => {
        getResult()
    })
</script>

<Heading>Result</Heading>
{#if result}
        <P>Task ID: {result.task_id}</P>
        <P>Status: {result.status}</P>
    {#if result.status == "running"}
        <Spinner />
    {:else}
        <P>Result: {result.result}</P>
    {/if}
{:else}
    <Spinner />
{/if}