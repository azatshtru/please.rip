<script>
    let active = false;
    let typing = false;

    function onKeyDown(e){
        switch(e.key){
            case "Enter":
                if(typing == true){
                    active = true;
                }
                break;
        }
    }

    function onKeyUp(e){
        switch(e.key){
            case "Enter":
                active = false;
                break;
        }
    }

    export let texts = [{sender: "Adwait", text: 'hi'}, {sender: "Tanushka", text: 'hi'}];
    export let roomcode = 'space';

</script>

<h3>💜 please.{roomcode}</h3>
{#each texts as text}
<p class="text"><span style="color:blueviolet; font-weight: bold">{text['sender']}</span> {text['text']}</p>
{/each}
<div class="textbox">
    <input class="field" on:focusout={() => {typing=false;}} on:focus={() => {typing=true;}} placeholder="text..">
    <button class="send" class:active={active}>send</button>
</div>

<svelte:window on:keyup={onKeyUp} on:keydown={onKeyDown} />

<style>
    @import url('https://fonts.googleapis.com/css2?family=Azeret+Mono:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

    h3 {
        text-align: start;
        margin-block: 0;
        margin-bottom: .5em;
        padding-left: 10px;
    }

    .text {
        color: black;
        text-align: left;
        padding-left: 10px;
        margin-block: 0px;
        padding-block: 0;
        line-height: 1.3em;
        font-family: 'Azeret Mono', monospace;
        font-size: .9em;
    }

    .textbox {
        display: flex; 
        flex-direction: row;
        justify-content: flex-start;
        align-items: center;

        width: 100%;
        gap: 5px;
    }

    .field {
        height: 30px;
        margin-left: 10px;
        margin-top: .8em;
        margin-bottom: 10px;
        background-color: whitesmoke;
        border: 2px solid black;
        font-family: 'Azeret Mono', monospace;
        color: black;
    }

    .field:focus {
        outline: none;
        cursor: text;
        color: black;
    }

    .send {
        height: fit-content;
        width: fit-content;
        
        background-color: rgb(199, 114, 255);
        border: 2px solid black;

        border-radius: 3px;
        padding-block: 4px;
        margin-right: 5px;

        font-family: 'Space Mono', monospace;
        color: black;

        box-shadow: 3px 3px black;
        position: relative;
        top: -2px;
    }

    .send:hover{
        border: 2px solid black;
    }

    .send:active, .active {
        box-shadow: none;
        position: relative;
        top: 3px;
        left: 3px;
    }
    
    .send:focus, .send:focus-visible {
        outline: none;
    }

</style>