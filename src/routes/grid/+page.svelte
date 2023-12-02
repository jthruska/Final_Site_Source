<!-- Java Script -->
<script>
    // @ts-ignore
    import AnimatedHeader from "../AnimatedHeader.svelte"
</script>



<!-- CSS -->
<style>
    .container1 {
        background-color: white;
        padding:1em;
        border-radius: 10px;
        border: 2pt gray dashed;

        display: grid;
        grid-template-columns: 1fr 1fr 2fr; 
    }

    .item1 {
        background-color: #314280;
        border-radius: 5px;
        color: white;
        font-size: 2em;
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        text-align: center;
        padding: 20px;
        border: 1px solid black;
        box-shadow: 3px 3px 5px rgba(0, 0, 0, 0.5), -2px -2px 3px rgba(0, 0, 0, 0.7) inset, 3px 3px 6px rgba(255, 255, 255, 0.7) inset;
    }
</style>



<!-- HTML -->
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grid</title>
</head>
<body>
    <AnimatedHeader selected="grid"/>

    <h1>Grid</h1>

    <div class="container1">
        <div class="item1 i1">1</div>
        <div class="item1">2</div>
        <div class="item1">3</div>
        <div class="item1">4</div>
        <div class="item1">5</div>
        <div class="item1">6</div>
        <div class="item1">7</div>
        <div class="item1">8</div>
        <div class="item1">9</div>
    </div>
</body>
</html>
