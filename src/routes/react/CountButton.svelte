<!-- Java Script -->
<script>
    /**
     * @type {number}
     */
     export let increment;
     export let bgc;
    let count = 0;

    const buttonStyle = "background-color:"+bgc+"; color:white; padding: 1em"

    function handleClick() {
        count += increment;
    }

    $: if (count > 10) {
        count = 0;
    }
</script>



<!-- CSS -->
<style>
    * {
        font-family: arial, Helvetica, sans-serif;
    }
</style>



<!-- HTML -->
<div>
    <button on:click={handleClick} style={buttonStyle}> 
        +{increment}
    </button> 
    
    <div>{count}</div>
</div>