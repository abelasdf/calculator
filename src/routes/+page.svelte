<script>
    let output = "0"; // Variable für die Anzeige der Berechnung bzw. des Resultats der Berechnung
    let a = 0;
    let b = 0;
    let operation = null;

    function setDigit(digit) {
        if (operation == null) {
            a = a * 10 + digit;
            output = a;
            // TODO: Dein Code
        } else{
            b = b * 10 + digit;
            output = a + operation + b;
            
        }
    }

    function setOperation(op) {
        console.log(op);
        
        if(b ==0){
            operation = op;
            output = output + operation;
        }
        else{
            calculate();
            operation = op;
            output = a + operation;
            
        }
        

        // TODO: Dein Code
    }

    function calculate() {
        console.log("calculate");
        if (operation == "+") {
            output = a + b;
            a = output;
        } else if (operation == "-") {
            output = a - b;
            a = output;
        } else if (operation == "*") {
            output = a * b;
            a = output;
        } else if (operation == "/") {
            output = a / b;
            a = output;
        }
        b = 0;
        // TODO: Dein Code
    }

    function allClear() {
        console.log("allClear");
        output = "0";
        a = 0;
        b = 0;
        operation = null;
        result = 0;
        // TODO: Dein Code
    }
</script>

<div class="calculator">
    <div id="display">{output}</div>

    <div class="keypad">
        <button
            class="key"
            on:click={() => {
                setDigit(7);
            }}>7</button
        >
        <button
            class="key"
            on:click={() => {
                setDigit(8);
            }}>8</button
        >
        <button
            class="key"
            on:click={() => {
                setDigit(9);
            }}>9</button
        >
        <button
            class="key operation"
            on:click={() => {
                setOperation("/");
            }}>/</button
        >

        <button
            class="key"
            on:click={() => {
                setDigit(4);
            }}>4</button
        >
        <button
            class="key"
            on:click={() => {
                setDigit(5);
            }}>5</button
        >
        <button
            class="key"
            on:click={() => {
                setDigit(6);
            }}>6</button
        >
        <button
            class="key operation"
            on:click={() => {
                setOperation("*");
            }}>*</button
        >

        <button
            class="key"
            on:click={() => {
                setDigit(1);
            }}>1</button
        >
        <button
            class="key"
            on:click={() => {
                setDigit(2);
            }}>2</button
        >
        <button
            class="key"
            on:click={() => {
                setDigit(3);
            }}>3</button
        >
        <button
            class="key operation"
            on:click={() => {
                setOperation("-");
            }}>-</button
        >

        <button
            class="key"
            on:click={() => {
                setDigit(0);
            }}>0</button
        >
        <button class="key operation" on:click={allClear}>AC</button>
        <button class="key operation" on:click={calculate}>=</button>
        <button
            class="key operation"
            on:click={() => {
                setOperation("+");
            }}>+</button
        >
    </div>
</div>

<style>
    /* Container-Element für den gesamten Rechner */
    .calculator {
        background-color: black;
        padding: 1em;
        /* Breite ohne padding: 4xTastenbreite + 3xGap */
        width: 13.5em;
    }

    /* Zahlenanzeige */
    #display {
        color: white;
        font-weight: bold;
        background-color: black;

        border: 1px solid white;
        padding: 0.5em;
        text-align: end;
        margin-bottom: 0.5em;
        font-family: "Courier New", Courier, monospace;
        font-size: 1.3em;
    }

    /* Tasten als Grid. Dokumentation zu Grid: https://www.w3schools.com/CSSref/pr_grid.asp */
    .keypad {
        display: grid;
        grid-template-columns: repeat(4, 3em);
        grid-template-rows: repeat(4, 3em);
        row-gap: 0.5em;
        column-gap: 0.5em;
    }

    /* Einzelne Tasten */
    .key {
        background-color: gray;
        color: white;
        font-family: "Courier New", Courier, monospace;
        font-size: 1.2em;
        font-weight: bold;

        justify-content: center;
        align-items: center;
        border-radius: 100%;
        border: none;
    }

    /* Mit der :active Pseudoklasse kann das Aussehen des Buttons verändert werden, solange er gedrückt wird.
     Siehe https://www.w3schools.com/cssref/sel_active.asp */
    .key:active {
        background-color: lightgrey;
    }

    /* Spezialfarbe für Operationstasten */
    .operation {
        background-color: orangered;
    }

    /* Aussehen eines gerade geklickten Operators (+,-,*,/) */
    .operation:active {
        background-color: white;
        color: orangered;
    }
</style>
