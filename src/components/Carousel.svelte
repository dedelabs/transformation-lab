<script>
  export let title = "Title for hero component"
  export let overtitle = "overtitle"
  export let slides = []
  export let slider = true
  export let type = 'Carousel'
  export let anchor
  export let shapes = 0
  export let colors = ['red', 'yellow', 'blue']

  import { swiperBreakpoints, swiperNavigation } from '../utilities.js'
  import { Navigation } from 'swiper'
  import { Swiper, SwiperSlide } from 'swiper/svelte'
  import Blobs from './Blobs.svelte'
  import SwiperNavigationButtons from './SwiperNavigationButtons.svelte'

  let HTMLanchor = anchor ? anchor : overtitle
  let baseClass = type.toLowerCase()
  let navigation =swiperNavigation(baseClass)
</script>

<div class="wrapper" id="{HTMLanchor}">
  <div class="{baseClass}">
    <div class="{baseClass}__overtitle">
      {overtitle}
    </div>
    {#if slider}
      <h3 class="{baseClass}__title">{@html title}</h3>
      <Swiper
        modules={[Navigation]}
        loop="{false}"
        navigation={navigation}
        class="{baseClass}__slides"
        spaceBetween={50}
        slidesPerView={3}
        breakpoints={swiperBreakpoints}
        on:slideChange={() => {}}
        on:swiper={(e) => {}}
      >
        {#each slides as slide}
          <SwiperSlide class="{baseClass}__slide">
            <div class="{baseClass}__slide__image">{@html slide.image}</div>
            <h4 class="{baseClass}__slide__title">{slide.title}</h4>
            {slide.description}
          </SwiperSlide>
        {/each}
      </Swiper>
      <SwiperNavigationButtons baseClass="{baseClass}"></SwiperNavigationButtons>
    {:else}
      <div class="{baseClass}__slides {baseClass}__slides--no-slider">
        {#each slides as slide}
          <div class="{baseClass}__slide">
            {@html slide.image}
            <h4 class="{baseClass}__slide__title">{slide.title}</h4>
            {slide.description}
          </div>
        {/each}
      </div>
    {/if}
  </div>
  <Blobs shapes={shapes} colors="{colors}"></Blobs>
</div>