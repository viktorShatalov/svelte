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
        types = lawyers.map((i) => i.types.map((y) => y.name));
        console.log(types);
    });
</script>

{#if lawyers.length}
    <ul class:item>
        {#each lawyers as item (item.id)}
            <li>
                <a href={linkToRegistration} target="_blank">
                    <span>
                        {item.date_start.split(".")[0].slice(11, -3)}
                    </span>
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
        width: 100%;
        max-width: 130px;
        margin: 0 auto 10px;
        display: inline-flex;
        align-items: center;
        border: 1px solid #ebeeee;
        background-color: #fddc03;
        border-radius: 10px;
        font-weight: 600;
        font-size: 13px;
        letter-spacing: 0.6px;
        padding: 10px 5px 10px 10px;
    }
    a {
        color: inherit;
        text-decoration: none;
    }
</style>
