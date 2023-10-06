<script lang="ts">
	import * as d3 from 'd3';
	import { onMount } from 'svelte';
	const barData = [45, 67, 96, 84, 41, 100];
	const rectWidth = 50;
	onMount(() => {
		const svg = d3.select('#container');
		svg
			.selectAll('rect')
			.data(barData)
			// calculate x-position based on its index;
			.attr('x', (d, i) => i * rectWidth)
			// set height based on the bound datum
			.attr('y', (d) => 100 - d)
			.attr('height', (d) => d)
			// rest of attributes are constant values
			.attr('width', rectWidth)
			.attr('stroke-width', 3)
			.attr('stroke', 'plum')
			.attr('fill', 'pink');
	});
</script>

<h1>D3 select petals</h1>

<br />

<svg id="container" width={rectWidth * barData.length} height="100" style="border: 1px dashed">
	<rect />
	<rect />
	<rect />
	<rect />
	<rect />
	<rect />
</svg>
