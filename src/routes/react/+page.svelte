<!-- Java Script -->
<script>
    // @ts-ignore
    import AnimatedHeader from "../AnimatedHeader.svelte"
    // @ts-ignore
    import CountButton from "./CountButton.svelte"
    // @ts-ignore
    import SearchBar from "./SearchBar.svelte"
</script>



<!-- HTML -->
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>React</title>
</head>
<body>
    <AnimatedHeader selected="react" />

    <div style="width:75%; margin:auto;">
        <h1>Replicating React with Svelte</h1>

        <div style="background-color:#e3ebf1; border-radius: 10px; padding: 1rem">
        
            <CountButton increment={1} bgc="#314280"/>
            <CountButton increment={2} bgc="#ff450b"/>
        
            <hr />
        
            <p>The source code for this project is on github repos for both creators: <a href="https://github.com/JasHruska406/Final_Site_Source"> Jasmine </a> and <a href="https://github.com/jthruska/Final_Site_Source"> Jesse </a> </p>
            
            <hr />
            
            <SearchBar />
        </div>

    </div>
</body>
</html>