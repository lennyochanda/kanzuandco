<script>
  import Hero from '$lib/components/Hero.svelte';
  import PromoBanner from '$lib/components/PromoBanner.svelte';
  import CategoryShowcase from '$lib/components/CategoryShowcase.svelte';
  import FeaturedGrid from '$lib/components/FeaturedGrid.svelte';
  import Footer from '$lib/components/Footer.svelte';
</script>

<Hero />

<PromoBanner />

<main>
  <CategoryShowcase />
  <FeaturedGrid />
</main>

<Footer />

<main>

</main>

<style>
  main {
    padding: 2rem;
  }
</style>
