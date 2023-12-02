<!-- Java Script -->
<script>
    export let selected = "calculator";
</script>



<!-- CSS -->
<style>
    header {
        display: flex;
        flex-wrap: wrap;
        width: 100%;
        align-items: center;
    }

    .item {
        background-color: #ffb8a2;
        color: black;
        padding: 20px;
        border: 1px solid white;
        width: 100%;
        text-align: center;
        font-size: larger;
        
        box-sizing: border-box;
        text-decoration: none;
    }

    .item:hover {
        transition: .4s linear;
        opacity: 85%;
    }

    .selected {
        background-color: #ff450b;
        color: white;
    }


    @media screen and (min-width: 600px) {
        .item {
            width: 25%;
        }
    }
</style>



<!-- HTML -->
<header>
    {#if selected == "calculator"}
        <a href="/" class="item selected" id="calc">Calculator</a>
    {:else}
        <a href="/" class="item" id="calc">Calculator</a>
    {/if}

    {#if selected == "react"}
        <a href="/react" class="item selected" id="react">React</a>
    {:else}
        <a href="/react" class="item" id="react">React</a>
    {/if}

    {#if selected == "sample"}
        <a href="/sample" class="item selected" id="sample">Sample</a>
    {:else}
        <a href="/sample" class="item" id="sample">Sample</a>
    {/if}

    {#if selected == "grid"}
        <a href="/grid" class="item selected" id="grid">Grid</a>
    {:else}
        <a href="/grid" class="item" id="grid">Grid</a>
    {/if}
</header>