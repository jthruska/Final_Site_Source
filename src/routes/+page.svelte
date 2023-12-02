<!-- Java Script -->
<script>
    import AnimatedHeader from "./AnimatedHeader.svelte"
    import SmallImage from "$lib/assets/machine640w.jpg"

    /**
     * @type {string}
     */
     let num1 = ""
     let num2 = ""
     let msg = ""
     let operator = ""
     let answer = ""
     
     let inp1c = "white"
     let inp2c = "white"


    function clear_ops() {
        inp1c = "white";
        inp2c = "white";

        msg = "";
        operator = " ";
        answer = "";
    }

    function clear() {
        clear_ops();
        num1 = "";
        num2 = "";
    }

    function getOperators() {
        const curNum1 = parseFloat(num1)
        const curNum2 = parseFloat(num2)
        let valid = true

        if (isNaN(curNum1)) {
            inp1c = "#ffb3b3";
            valid = false
        }
        else {
            inp1c = "white";
        }
        if (isNaN(curNum2)) {
            inp2c = "#ffb3b3";
            valid = false
        }
        else {
            inp2c = "white";
        }

        if (valid) {
            msg = "";
            return [curNum1, curNum2];
        }
        else {
            msg = 'Invalid input';
            return undefined;
        }
    }

    function add() {
        let nums = getOperators();
        operator = "+";
        answer = nums!=undefined ? (nums[0] + nums[1]).toString() : '?';
    }

    function subtract() {
        let nums = getOperators();
        operator = "-";
        answer = nums!=undefined ? (nums[0] - nums[1]).toString() : '?';
    }

    function multiply() {
        let nums = getOperators();
        operator = "×";
        answer = nums!=undefined ? (nums[0] * nums[1]).toString() : '?';
    }

    function divide() {
        let nums = getOperators();
        operator = "÷";
        answer = nums!=undefined ? (nums[0] / nums[1]).toString() : '?';
    }

    function greater() {
        let nums = getOperators();
        operator = "≥";
        answer = nums!=undefined ? (nums[0] >= nums[1]).toString() : '?';
    }

    function less() {
        let nums = getOperators();
        operator = "≤";
        answer = nums!=undefined ? (nums[0] <= nums[1]).toString() : '?';
    }
</script>



<!-- CSS -->
<style>
    #nums {
        display: flex;
        flex-wrap: wrap;
        width: 100%;
        align-items: center;
    }

    #banner {
        width: 100%;
    }

    button:hover {
        transition: .4s linear;
        opacity: 85%;
    }

    #eq, .hdn_btn {
        display: none;
    }

    input {
        font-size: 3.2em;
        width: 100%;
        margin: auto;
    }

    label, #message {
        height: 200%;
        font-size: 2rem;
    }

    #answer {
        font-size: 3.2rem;
    }

    #buttons {
        display: grid;
        grid-template-columns: 1fr 1fr; 
        grid-template-rows: 1fr 1.4fr;

        width: 50%;
        margin: auto;
    }

    .op_button {
        box-sizing: border-box;

        background-color: #314280;
        color: white;
        border-radius: 100%;
        text-align: center;

        width: 80%;
        margin: auto;

        font-size: 4em;
        aspect-ratio : 1 / 1;
    }

    @media screen and (min-width: 600px) {
        #message, input, label, #answer {
            font-size: 1.2rem;
        }

        #banner {
            content: url("$lib/assets/machine1280w.jpg");
        }
        
        .hdn_btn, #eq {
            display: unset;
        }

        input {
            font-size: unset;
            width: unset;
            margin: unset;
        }

        #message, #nums {
            width: 90%;
            margin: auto;
        }

        #buttons {
            grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 4fr;
            width: 600px;
            margin: auto;
            margin-left: 5%;
        }

        .op_button {
            width: 35px;
            
            align-self: left;
            font-size: 1.3em;
        }
}
</style>



<!-- HTML -->
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <script src="/lib/index" defer></script>
</head>
<body>
    <AnimatedHeader selected="calculator"/>

    <img id="banner" src={SmallImage} alt="machine with numbers on its surface">

    <p id="message"> {msg} </p>
    <br class="hdn_btn">

    <div id="nums">        

        <input type="number" id="val1" bind:value={num1} style="background-color:{inp1c}"/>

        <!-- svelte-ignore a11y-label-has-associated-control -->
        <label> &nbsp;&nbsp; <label id="op"> {operator} </label> &nbsp;&nbsp; </label>

        <input type="number" id="val2" bind:value={num2} style="background-color:{inp2c}"/>

        <!-- svelte-ignore a11y-label-has-associated-control -->
        <label id="eq"> &nbsp;&nbsp;&nbsp;=&nbsp;&nbsp;&nbsp; </label>

        <!-- svelte-ignore a11y-label-has-associated-control -->
        <label id="answer"> {answer} </label>

    </div>

    <br>
    
    <div id="buttons">
        <button class="op_button hdn_btn" id="clear" on:click={clear}>C</button>
        <button class="op_button" id="plus" on:click={add}>+</button>
        <button class="op_button" id="minus" on:click={subtract}>&minus;</button>
        <button class="op_button" id="times" on:click={multiply}>&times;</button>
        <button class="op_button" id="divide" on:click={divide}>&divide;</button>
        <button class="op_button hdn_btn" id="greater" on:click={greater}>&ge;</button>
        <button class="op_button hdn_btn" id="less" on:click={less}>&le;</button>
    </div>
</body>
</html>
