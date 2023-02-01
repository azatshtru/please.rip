<script>
  import Draggable from "./lib/Draggable.svelte";
  import Room from "./lib/Room.svelte";

  let joined = false;
  let username = '';
  let roomcode = '';

  function joinRoom () {
    username = username.trim();
    roomcode = roomcode.trim();
    if(username == '' || roomcode == ''){ 
      return; 
    }
    joined = true;
  }

</script>

<main>
  <h1>please.rip</h1>
  {#if !joined}
  <Draggable>
    <div class="dragbox">
      <div class="header"></div>
      <input class="field" placeholder="username" bind:value={username}>
      <input class="field" placeholder="roomcode" bind:value={roomcode}>
      <button class="submit" on:click={joinRoom}>Join Room</button>
    </div>
  </Draggable>
  {:else}
  <Draggable>
    <div class="dragbox" style="width: 320px;">
      <div class="header"></div>
      <Room roomcode={roomcode} />
    </div>
  </Draggable>
  {/if}

</main>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=Azeret+Mono:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

  .header {
    background-color: black;
    width: 100%;
    height: 25px;
    margin-bottom: 10px;
  }

  .dragbox {
    width: 300px;
    height: fit-content;
    display: flex;
    flex-direction: column;
    background-color: whitesmoke;
    padding-bottom: 3px;
    border: 2px solid black;
  }

  .field {
    height: 40px;
    margin-inline: 10px;
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

  .submit {
    margin-inline: 10px;
    margin-block: 10px;
    border-radius: 0px;
    font-family: 'Space Mono', monospace;
    scale: 100%;
  }

  .submit:hover {
    background-image: linear-gradient(to right, black 30%, rgb(154, 13, 255)50%, rgb(0, 0, 0) 85%);
    background-size: 400%;
    animation: gradientshift .8s linear;
    scale: 102%; 
  }

  h1 {
    font-family: 'Space Mono', monospace;
  }

  @keyframes gradientshift {
    0% {
      background-position: 0%;
    }
    100%{
      background-position: 150%;
    } 
  }
</style>
