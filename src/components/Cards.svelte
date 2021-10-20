<script>
  export let title = "Title for hero component";
  export let overtitle = "overtitle";
  export let cards = [];
  export let slider = false;
  export let anchor;

  let HTMLanchor = anchor ? anchor : overtitle;

  let navigation = { nextEl: '.cards__next' }
  
  import { Navigation } from 'swiper'
  import { Swiper, SwiperSlide } from 'swiper/svelte'
  import { swiperBreakpoints } from '../utilities.js'
</script>

<div class="wrapper" id="{HTMLanchor}">
  <div class="cards">
    <div class="cards__overtitle">{overtitle}</div>
    <h3 class="cards__title">{title}</h3>
    {#if slider}
      <Swiper
        modules={[Navigation]}
        loop="{true}"
        navigation={navigation}
        class="cards__container"
        spaceBetween={50}
        slidesPerView={3}
        breakpoints={swiperBreakpoints}
        on:slideChange={() => {}}
        on:swiper={(e) => {}}
      >
        {#each cards as card}
          <SwiperSlide>
            <div class="cards__card">
              <h4 class="cards__card__title">{@html card.title}</h4>
              {card.description}
            </div>
          </SwiperSlide>
        {/each}
      </Swiper>
      <div class="cards__next">Next -></div>
    {:else}
      <div class="cards__container">
        {#each cards as card}
          <div class="cards__card">
            <h4 class="cards__card__title">{@html card.title}</h4>
            {card.description}
          </div>
        {/each}
      </div>
    {/if}
  </div>
</div>