<script>
  import Notification from '$lib/components/Notification.svelte';
  import Navigation from '$lib/components/Navigation.svelte';
  import Hero from '$lib/components/Hero.svelte';
</script>

<Notification />
<Navigation />
<Hero />

<main>
  <h1>Welcome to SvelteKit</h1>
  <p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>
</main>

<style>
  main {
    padding: 2rem;
  }
</style>
