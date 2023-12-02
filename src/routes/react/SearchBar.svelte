<!-- Java Script -->
<script>
// @ts-nocheck

    import { onMount } from 'svelte';
    
    const prodStyle =
        `border: 2px solid gray;
        border-radius: 10px;
        width: 100px;
        padding: 1rem;
        overflow: auto;
        margin: 1rem;
        background-color: white`

    /**
     * @type {any[]}
     */
    let products = [];
    /**
     * @type {string | any[]}
     */
    let filteredProducts = [];
    let searchTerm = '';
    
    // fetching the API data
    const fetchData = async () => {
        const response = await fetch('https://fakestoreapi.com/products');
        products = await response.json();
        filterProducts();
    };
    
    // function to filter the products based on the search term
    const filterProducts = () => {
        filteredProducts = products.filter(product =>
            product.title.toLowerCase().includes(searchTerm.toLowerCase())
        );
    };
  
    onMount(fetchData);
    
    $: filterProducts(); // Initial filter
  
    /**
     * @param {{ target: { value: string; }; }} event
     */
    function handleInput(event) {
        searchTerm = event.target.value;
        filterProducts();
    }
</script>



<!-- HTML -->
<div>
    <input bind:value={searchTerm} on:input={handleInput} placeholder="Search products" />

    {#if filteredProducts.length > 0}
        <div style="display:flex; flex-flow: row wrap">
            {#each filteredProducts as product (product.id)}
                <div style={prodStyle}>
                    <p>{product.title}</p>
                    <p>${product.price}</p>
                    <img style="width: 100%" src={product.image} alt={product.title} />
                </div>
            {/each}
        </div>
    {:else}
        <p>No matching products found.</p>
    {/if}
</div>