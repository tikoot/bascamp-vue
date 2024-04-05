<template>
  <section
    class="px-6 pt-[21px] pb-[35px] rounded-2xl bg-white col-span-2 min-[1240px]:cols-span-3"
  >
    <div class="mb-[20px]">
      <h1>ცნობილი ფაქტები</h1>
    </div>
    <swiper
      :cssMode="true"
      :navigation="true"
      :keyboard="true"
      :modules="modules"
      :slidesPerView="slidesPerView"
      :spaceBetween="30"
      class="mySwiper factsSlider"
    >
      <swiper-slide class="h-[200px] bg-[#F5F8FF] px-3 rounded-[20px]">
        <div class="bg-[#F5F8FF]">
          <img src="../assets/pic2.png" alt="" />
          <h2 class="text-start text-base mt-2">
            ქვემო ქართლის რეგიონში 20 მლნ ლარამდე ღირებულების
          </h2>
        </div></swiper-slide
      >
      <swiper-slide class="h-[200px] bg-[#F5F8FF] px-3 rounded-[20px]">
        <div class="bg-[#F5F8FF]">
          <img src="../assets/pic2.png" alt="" />
          <h2 class="text-start text-base mt-2">
            ქვემო ქართლის რეგიონში 20 მლნ ლარამდე ღირებულების
          </h2>
        </div></swiper-slide
      >
      <swiper-slide class="h-[200px] bg-[#F5F8FF] px-3 rounded-[20px]">
        <div class="bg-[#F5F8FF]">
          <img src="../assets/pic2.png" alt="" />
          <h2 class="text-start text-base mt-2">
            ქვემო ქართლის რეგიონში 20 მლნ ლარამდე ღირებულების
          </h2>
        </div></swiper-slide
      >
      <swiper-slide class="h-[200px] bg-[#F5F8FF] px-3 rounded-[20px]">
        <div class="bg-[#F5F8FF]">
          <img src="../assets/pic2.png" alt="" />
          <h2 class="text-start text-base mt-2">
            ქვემო ქართლის რეგიონში 20 მლნ ლარამდე ღირებულების
          </h2>
        </div></swiper-slide
      >
      <swiper-slide class="h-[200px] bg-[#F5F8FF] px-3 rounded-[20px]">
        <div class="bg-[#F5F8FF]">
          <img src="../assets/pic2.png" alt="" />
          <h2 class="text-start text-base mt-2">
            ქვემო ქართლის რეგიონში 20 მლნ ლარამდე ღირებულების
          </h2>
        </div></swiper-slide
      >
      <swiper-slide class="h-[200px] bg-[#F5F8FF] px-3 rounded-[20px]">
        <div class="bg-[#F5F8FF]">
          <img src="../assets/pic2.png" alt="" />
          <h2 class="text-start text-base mt-2">
            ქვემო ქართლის რეგიონში 20 მლნ ლარამდე ღირებულების
          </h2>
        </div></swiper-slide
      >
    </swiper>
  </section>
</template>
<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";
import "../tailwind.css";
import { Navigation } from "swiper/modules";

export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      modules: [Navigation],
      slidesPerView: 1.2,
    };
  },
  mounted() {
    this.updateSlidesPerView();
    window.addEventListener("resize", this.updateSlidesPerView);
  },
  methods: {
    updateSlidesPerView() {
      const breakpoints = {
        0: 1.2,
        768: 2.2,
        1024: 2.5,
        1240: 3,
      };
      const windowWidth = window.innerWidth;
      let newSlidesPerView = this.slidesPerView;

      Object.keys(breakpoints).forEach((breakpoint) => {
        if (windowWidth >= breakpoint) {
          newSlidesPerView = breakpoints[breakpoint];
        }
      });

      this.slidesPerView = newSlidesPerView;
    },
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.updateSlidesPerView);
  },
};
</script>
