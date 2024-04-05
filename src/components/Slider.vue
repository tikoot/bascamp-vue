<template>
  <div
    class="swiper-container bg-white max-w-[1032px] p-3 rounded-[20px] col-span-2"
  >
    <swiper
      :cssMode="true"
      :navigation="true"
      :pagination="{
        clickable: true,
      }"
      :mousewheel="true"
      :keyboard="true"
      :modules="modules"
      class="mainSlider"
    >
      >
      <swiper-slide v-for="(item, index) in newsItems" :key="index">
        <div>
          <div class="relative">
            <img
              :src="item.image"
              alt="News Image"
              class="w-full h-32 object-cover mb-4"
            />
          </div>
          <div>
            <div class="flex">
              <div
                class="text-[#1D2D35] text-xs font-bold bg-[#F5F8FF] rounded-2xl py-[6px] px-2"
              >
                {{ item.releaseDate }}
              </div>
              <div
                class="text-[#1D2D35] text-xs font-bold bg-[#F5F8FF] rounded-2xl py-[6px] px-2"
              >
                {{ item.category }}
              </div>
            </div>

            <h2 class="text-2xl text-[#1D2D35] font-semibold mt-2 text-start">
              {{ item.title }}
            </h2>
            <p class="mt-2 text-base text-[#657178] text-start hidden md:block">
              {{ item.description }}
            </p>
          </div>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
import { Swiper, SwiperSlide } from "swiper/vue";

import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";

import "../tailwind.css";

import { Navigation, Pagination, Mousewheel, Keyboard } from "swiper/modules";

export default {
  components: {
    Swiper,
    SwiperSlide,
  },

  computed: {
    newsItems() {
      return this.$store.getters.getNewsItems;
    },
  },
  setup() {
    return {
      modules: [Navigation, Pagination, Mousewheel, Keyboard],
    };
  },
};
</script>
