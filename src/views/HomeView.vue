<template>
  <div class="mx-auto">
    <Navbar />
    <main class="container mx-auto pt-[42px] pb-40">
      <div class="grid grid-cols-2 min-[1240px]:grid-cols-3 gap-x-8">
        <Slider />
        <AllNews class="min-[1240px]:block hidden" />
      </div>
      <div
        class="md:grid md:grid-cols-2 mt-12 md:gap-x-8 flex flex-col min-[1240px]:hidden"
      >
        <AllNews />
        <Popular />
      </div>
      <div class="min-[1240px]:grid min-[1240px]:grid-cols-3 gap-x-8 mt-12">
        <div class="min-[1240px]:col-span-2">
          <Facts />
          <Article />
        </div>
        <Popular class="min-[1240px]:block hidden" />
      </div>
    </main>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import Slider from "@/components/Slider.vue";
import AllNews from "@/components/AllNews.vue";
import Facts from "@/components/Facts.vue";
import Popular from "@/components/Popular.vue";
import Article from "@/components/Article.vue";

export default {
  components: {
    Navbar,
    Slider,
    AllNews,
    Facts,
    Popular,
    Article,
  },
};
</script>
