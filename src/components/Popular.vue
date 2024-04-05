<template>
  <section
    class="bg-white rounded-[20px] pt-[24px] px-[12px] pb-[14px] min-[1240px]:h-[564px] mt-6 md:mt-0"
  >
    <h1 class="text-[#1D2D35] text-[20px] pb-6 font-semibold">პოპულარული</h1>
    <div class="overflow-y-auto min-[1240px]:max-h-[470px] max-h-[330px]">
      <div
        v-for="item in allNews"
        :key="item.id"
        class="flex items-center justify-start border-b-2 border-dashed border-[#F0F4F5] pb-4 mb-4"
      >
        <div class="flex items-center">
          <img src="../assets/moon.png" alt="clock logo" />
        </div>
        <p class="text-start pl-2 max-w-[188px]">
          {{ item.description }}
        </p>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  computed: {
    allNews() {
      return this.$store.getters.getAllNews;
    },
  },
};
</script>
