<template>
  <section class="bg-white rounded-[20px] pt-[24px] px-[12px] pb-[14px]">
    <h1 class="text-[#1D2D35] text-[20px] pb-6 font-semibold">ყველა სიახლე</h1>
    <div class="overflow-y-auto min-[1240px]:max-h-[550px] max-h-[330px]">
      <div v-for="item in allNews" :key="item.id">
        <div class="flex items-center">
          <img src="../assets/clock.png" alt="clock logo" />
          <p class="text-xs text-[#585EE3] font-bold pl-1">
            {{ item.releaseHour }} &#x2022; {{ item.releaseDate }}
          </p>
        </div>
        <p
          class="text-start pt-2 pb-4 mb-4 border-b-2 border-dashed border-[#F0F4F5]"
        >
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
