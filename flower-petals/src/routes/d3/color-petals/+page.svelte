<script lang="ts">
	import * as d3 from 'd3';
	import { onMount } from 'svelte';
	import movies from '../../../lib/movies.json';
	let petalPath = 'M0,0 C50,40 50,70 20,100, L0,85 L-20,100 C-50,70 -50,40 0,0';

	function genreToColor(genre: 'Action' | 'Comedy' | 'Animation' | 'Drama' | 'Other') {
		switch (genre) {
			case 'Action':
				return '#FFC8F0';
			case 'Comedy':
				return '#cbf2bd';
			case 'Animation':
				return '#afe9ff';
			case 'Drama':
				return '#ffb09e';
			case 'Other':
				return '#fff2b4';
			default:
				break;
		}
	}

	onMount(() => {
		d3.select('#container')
			.selectAll('path')
			.data(movies.map((m) => m.genres[0]))
			.attr('fill', (d) => genreToColor(d as any));
	});
</script>

<h1>D3 select petals</h1>

<br />

<svg id="container" width="500" height="100" style="border: 1px dashed">
	<path d={petalPath} transform="translate(50, 0)" />
	<path d={petalPath} transform="translate(150, 0)" />
	<path d={petalPath} transform="translate(250, 0)" />
	<path d={petalPath} transform="translate(350, 0)" />
	<path d={petalPath} transform="translate(450, 0)" />
</svg>
