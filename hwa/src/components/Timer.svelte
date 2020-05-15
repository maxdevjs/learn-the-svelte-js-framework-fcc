<script>
  import ProgressBar from './ProgressBar.svelte'
  import { createEventDispatcher } from 'svelte';

  const totalSeconds = 20;
  let secondLeft = totalSeconds;
  let disabled = false;
  let opacity = 1;
  const dispatch = createEventDispatcher();

  const startTimer = () => {
    disabled = true;
    const timer = setInterval(() => {  
      secondLeft -= 1;
        opacity = Math.random() + 0.2;
      if (secondLeft === 0 ) {
        clearInterval(timer);
        disabled = false;
        secondLeft = totalSeconds;
        opacity = 1;
        dispatch('end');
      }
    }, 1000);
    
  };  
</script>

<div bp="grid">
  <h2 bp="offset-5@md 4@md 12@sm">Seconds Left: {secondLeft}</h2>
</div>

<ProgressBar progress={secondLeft} {opacity} />

<div bp="grid">
  {#if disabled === false}
  <button bp="offset-5@md 4@md 12@sm" class="button start" on:click={startTimer} {disabled}>Start</button>
  {:else}
    <div bp="offset-5@md 4@md 12@sm" class="button button-disabled start">
      wash those dirty hands
    </div>
  {/if}
</div>


<style>
  h2 {
    margin: 0;
  }
  .start {
    background-color: rgb(154, 73, 73);
    width: 100%;
    margin: 10px 0;
  }

  .button-disabled {
    cursor: not-allowed; 
  }
</style>