<script>
  import {tweened} from 'svelte/motion';
  
  export let progress = 0;
  export let opacity;

  const tweenedProgress = tweened(100, {duration: 1000});
  const tweenedOpacity = tweened(1, {duration: 1000});

  $: tweenedProgress.set(progress * 5);
  $: tweenedOpacity.set(opacity);
</script>

<div bp="grid">
  <div bp="offset-5@md 4@md 12@sm" class="progress-container">
    <div class="progress-bar" style="width: {$tweenedProgress}%; background-color: rgba(77, 199, 55, {$tweenedOpacity});">
      <span class="sr-only">{progress}%</span>
    </div>
  </div>
</div>

<style>
  .progress-container {
    margin: 20px 0;
    border: solid rgb(190, 190, 190) 1px;
  }
  .progress-bar {
    height: 30px;
    background-color: rgba(77, 199, 55, 1);
  }
</style>