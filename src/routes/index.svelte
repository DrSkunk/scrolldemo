<script>
	import { onMount } from 'svelte';

	const filler = new Array(1000);

	const speeds = [-1000, -100, -50, -25, -10, -5, -1, 0, 1, 5, 10, 25, 50, 100, 1000];
	let speed = 0;

	const setSpeed = (newSpeed) => {
		speed = newSpeed;
	};

	onMount(() => {
		setInterval(() => {
			window.scrollBy({
				top: speed,
				behavior: 'smooth'
			});
		}, 10);
	});
</script>

<div class="sticky top-0">
	{#each speeds as speed}
		<button class="border mx-4 my-2 bg-indigo-200" on:click={() => setSpeed(speed)}
			>Speed {speed}</button
		>
	{/each}
</div>
<h1 class="text-3xl font-bold underline">Scrolling</h1>

{#each filler as _, i}
	<div class="text-6xl">
		Hello world!
		{i}
	</div>
{/each}
