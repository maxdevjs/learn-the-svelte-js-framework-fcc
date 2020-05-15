<script>
	import Timer from './components/Timer.svelte'
	import HowTo from './components/HowTo.svelte'

	let audio;

	const timerEnds = (e) => {
		audio.play();
	};
</script>

<h1>Handwashing App</h1>

<Timer  on:end={timerEnds} />
<HowTo />
<h3>
	<a href="https://www.who.int/gpsc/clean_hands_protection/en/">Picture Source</a> | 
	<a href="https://freesound.org/people/metrostock99/sounds/345086/">Sound Source</a>
</h3>

<audio bind:this={audio}>
	<source src="sound/sound.wav" />
</audio>

<style>
	h1, h3 {
		text-align: center;
	}
</style>