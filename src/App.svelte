<script>
	import data from './_data.json'
	import "swiper/css/navigation"
  import 'swiper/css'

	import { BgCards, BlockWithImage, Bubbles, Cards, Carousel, Hero, Spacer, Text, Title } from 'dede-svelte-components'

	import Footer from './components/Footer.svelte'
	import Header from './components/Header.svelte'

	let loadedComponents = {
		"BgCards": BgCards,
		"BlockWithImage": BlockWithImage,
		"Bubbles": Bubbles,
		"Cards": Cards,
		"Carousel": Carousel,
		"Hero": Hero,
		"Spacer": Spacer,
		"Text": Text,
		"Title": Title
	}
	
	// Hardcoded before routing
	$: components = data.pages.filter((p) => p.name == 'Home')[0].components;

	$: colors = data.colorPalette;
</script>

<main>
	<Header></Header>
	{#each components as component}
		<svelte:component this={loadedComponents[component.type]} {...component} colors="{colors}" />
	{/each}
	<Footer></Footer>
</main>