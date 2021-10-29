<script>
  export let overtitle = "overtitle"
  export let title = "Title for hero component"
  export let bubbles = ['first', 'second', 'third']
  export let slider = false
  export let anchor
  export let type = 'Bubbles'
  export let shapes = 0
  export let colors = ['red', 'yellow', 'blue']

  import { generateBlob } from '../utilities.js'
  import { Navigation } from 'swiper'
  import { Swiper, SwiperSlide } from 'swiper/svelte'
  import Blobs from './Blobs.svelte'
  import SwiperNavigationButtons from './SwiperNavigationButtons.svelte'
  import { swiperBreakpoints, swiperNavigation } from '../utilities.js'

  let HTMLanchor = anchor ? anchor : overtitle;
  let baseClass = type.toLowerCase()
  let navigation =swiperNavigation(baseClass)
</script>

<div class="wrapper" id="{HTMLanchor}">
  <div class="{baseClass}">
    <div class="{baseClass}__overtitle">{overtitle}</div>
    <h3 class="{baseClass}__title">{@html title}</h3>
    {#if slider}
      <div class="{baseClass}__bubbles">
        <Swiper
          modules={[Navigation]}
          loop="{false}"
          navigation={navigation}
          class="{bubbles}__slides"
          spaceBetween={50}
          slidesPerView={4}
          breakpoints={swiperBreakpoints}
          on:slideChange={() => {}}
          on:swiper={(e) => {}}
        >
          {#each bubbles as bubble}
            <SwiperSlide>
              <div class="{baseClass}__bubble">
                <div class="{baseClass}__bubble__text">{bubble.text}</div>
                <div class="{baseClass}__bubble__bg" style="border-radius: {generateBlob()}; background-color: {bubble.color}"></div>
                <div class="{baseClass}__bubble__bg-out" style="border-radius: {generateBlob()}; background-color: {bubble.color}"></div>
              </div>
            </SwiperSlide>
          {/each}
        </Swiper>
      </div>
      <SwiperNavigationButtons baseClass="{baseClass}"></SwiperNavigationButtons>
    {:else}
      <div class="{baseClass}__bubbles">
        {#each bubbles as bubble}
          <div class="{baseClass}__bubble-container">
            <div class="{baseClass}__bubble">
              <div class="{baseClass}__bubble__text">{bubble.text}</div>
              <div class="{baseClass}__bubble__bg" style="border-radius: {generateBlob()}; background-color: {bubble.color}"></div>
              <div class="{baseClass}__bubble__bg-out" style="border-radius: {generateBlob()}; background-color: {bubble.color}"></div>
            </div>
          </div>
        {/each}
      </div>
    {/if}
  </div>
  <Blobs shapes={shapes} colors="{colors}"></Blobs>
</div>