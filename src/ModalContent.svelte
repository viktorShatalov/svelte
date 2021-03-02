<script>
    import { onMount } from "svelte";

    // classes
    const item = "item";
    // end classes

    let lawyer;
    let lawyers = [];
    let types = [];

    const baseUrl = "https://api-esqfind.4px.site";

    let date_start = new Date().toJSON().split("T")[0];
    let date_end = new Date(new Date().setDate(new Date().getDate() + 10))
        .toJSON()
        .split("T")[0];

    let lawyerID = "test-user";
    let linkToRegistration = "https://esqfind-dev.appclose.info/user/sign-up";

    onMount(async () => {
        const res = await fetch(
            `${baseUrl}/view/lawyer/${lawyerID}/schedule?date_start=${date_start}&date_end=${date_end}`
        ).catch((error) => console.log(error));
        lawyer = await res.json();
        lawyers = Object.values(lawyer)[0];
        types = lawyers.map((i) => i.types.map((item) => item.name));
        console.log(types);
    });
</script>

{#if lawyers.length}
    <ul class:item>
        {#each lawyers as item (item.id)}
            <li>
                <a href={linkToRegistration} target="_blank">
                    <span>
                        {item.date_start.split(".")[0].slice(14)}
                    </span>
                    <span>{types}</span>
                </a>
            </li>
        {/each}
    </ul>
{:else}
    <p>loading...</p>
{/if}

<style>
    .item {
        list-style: none;
        padding-bottom: 20px;
        padding: 0;
    }
    .item li {
        padding-bottom: 20px;
    }
</style>
