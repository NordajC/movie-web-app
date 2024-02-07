<script>
	console.log(1);
	import { onMount } from 'svelte';
	let movies = [];
	let movieType = 'new'; // Use 'new' for new releases or 'add' for recently added
	let pageNumber = '1'; // Leave empty or specify a page number
	const options = {
		method: 'GET',
		headers: {
			accept: 'application/json',
			Authorization:
				'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJmM2ZkMTRlNzM0MmJmODAxYjlkNGFjMTQ0NTdlMGNmMiIsInN1YiI6IjY1YzBkMTcwYTM1YzhlMDE2M2Q2NDFlOCIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.zKuClwiAwCzOcxlsoObHj9Rci1GiPZLTlVbXR_2Jodw'
		}
	};
	console.log(2);
	onMount(async () => {
		const url = `https://vidsrc.to/vapi/movie/${movieType}/${pageNumber}`;
		try {
			const response = fetch('https://api.themoviedb.org/3/movie/changes?page=1', options)
				.then((response) => response.json())
				.then((response) => console.log(response))
				.catch((err) => console.error(err));

			if (response.ok) {
				try {
					const data = await response.json();
					movies = data;
				} catch (error) {
					console.error('Error parsing response: ', error);
				}
			} else {
				console.error('Failed to fetch movies: ', response.status);
			}
		} catch (error) {
			console.error('Error fetching movies: ', error);
		}
	});
	console.log(3);
	console.log(movies);
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<iframe
	src="https://vidsrc.to/embed/movie/385687"
	width="560"
	height="315"
	frameborder="0"
	allowfullscreen
></iframe>

<div>
	{#if movies.length > 0}
		<h2>Latest Movies</h2>
		<ul class="movie-list">
			{#each movies as movie}
				<li class="movie">
					<strong>{movie.title}</strong>
					<!-- Add more movie details here as needed -->
				</li>
			{/each}
		</ul>
	{:else}
		<p>Loading movies...</p>
	{/if}
</div>

<style>
	/* Add some basic styling */
	.movie-list {
		list-style-type: none;
		padding: 0;
	}
	.movie {
		margin-bottom: 1rem;
		padding: 0.5rem;
		border: 1px solid #ccc;
		border-radius: 4px;
	}
</style>
