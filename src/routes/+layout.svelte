<script>
	import '../app.css';
    import "@picocss/pico/css/pico.min.css";
</script>
<main>
	<slot />
</main>

<footer>
	<p>Hashpoll is released under the MIT License.</p>
</footer>

<style>
    main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 1024px;
		margin: 0 auto;
		box-sizing: border-box;
	}
    footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 40px;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 40px 0;
		}
	}
</style>
