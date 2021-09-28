<script>
	import Login from './Login.svelte'
	let user = null

    async function logout(e) {
        user = null
    }
</script>

<main>
	<h1>Biarbala<sub>Admin</sub></h1>
	{#if user}
		<h2>hello {user.name}<a class="logout" on:click={logout}>Log out</a></h2>
	{:else}
		<Login bind:user/>
	{/if}
</main>

<style>
	main {
		text-align: center;
		padding: 2rem;
		margin: 0 auto;
	}

	h1 {
		color: rgb(118, 121, 122);
		text-transform: uppercase;
		font-size: 8rem;
		font-weight: 100;
	}

	h1 > sub {
		font-weight: lighter;
		font-size: 0.8rem;
	}
	

    .logout {
		font-weight: lighter;
		font-size: 1.2rem;
        color: rgb(104, 112, 112);
        margin-left: 1rem;
        transition: color 350ms;
        cursor: default;
	}
    .logout:hover {
        color: black;
    }
	:root { font-size: calc(1vw * 2); }
	/* @media (max-width: 440px) { :root { font-size: calc(1vw / 40); }}
	@media (max-width: 460px) { :root { font-size: calc(5vw / 40); }}
	@media (max-width: 480px) { :root { font-size: calc(15vw / 40); }}
	@media (max-width: 500px) { :root { font-size: calc(20vw / 40); }}
	@media (max-width: 520px) { :root { font-size: calc(30vw / 40); }}
	@media (max-width: 560px) { :root { font-size: calc(35vw / 40); }}
	@media (max-width: 600px) { :root { font-size: calc(45vw / 40); }}
	@media (max-width: 640px) { :root { font-size: calc(55vw / 40); }}
	@media (max-width: 700px) { :root { font-size: calc(65vw / 40); }}
	@media (max-width: 740px) { :root { font-size: calc(75vw / 40); }}
	@media (max-width: 780px) { :root { font-size: calc(80vw / 40); }} */
</style>