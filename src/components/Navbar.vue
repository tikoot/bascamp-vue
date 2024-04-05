<template>
  <header class="bg-white flex flex-col">
    <nav
      class="flex items-center justify-between py-9 container mx-auto px-4 md:px-0"
      ref="navbar"
    >
      <div class="flex items-center">
        <div class="flex items-center">
          <a href="#" class="-m-1.5 p-1.5">
            <img class="h-8 w-auto pr-6" :src="logoImg" alt="Company Logo" />
          </a>

          <div class="h-8 w-[2px] bg-[#F0F4F5] mr-8"></div>
        </div>

        <div class="hidden min-[1240px]:flex xl space-x-6">
          <template
            v-for="(category, index) in displayedCategories"
            :key="index"
            class="text-sm font-semibold leading-6 text-[#657178] category-item max-w-[500px]"
          >
            <a
              href="#"
              class="text-base font-semibold leading-6 text-[#657178] category-item"
              >{{ category }}</a
            >
          </template>

          <div
            v-if="hiddenCategories.length > 0"
            class="relative"
            @mouseover="showDropdown"
          >
            <a
              href="#"
              class="text-base font-semibold leading-6 text-[#657178] flex items-center"
              >სხვა <img src="../assets/arr.png" alt="" class="ml-2"
            /></a>
            <div
              v-show="isDropdownVisible"
              class="absolute mt-2 w-48 rounded-md bg-white shadow-lg z-50"
              @mouseleave="hideDropdown"
            >
              <div
                class="py-1"
                role="menu"
                aria-orientation="vertical"
                aria-labelledby="options-menu"
              >
                <a
                  v-for="(category, index) in hiddenCategories"
                  :key="index"
                  href="#"
                  class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100"
                  role="menuitem"
                  >{{ category }}</a
                >
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="flex items-center">
        <img
          :src="searchImg"
          alt="search Logo"
          class="bg-[#F5F8FF] p-2 rounded-full md:hidden"
        />
        <div
          class="min-[1240px]:flex-1 lg:justify-end items-center md:flex hidden"
        >
          <a href="#" class="bg-[#F5F8FF] p-2 rounded-full"
            ><img :src="instaImg" alt=""
          /></a>
          <a href="#" class="bg-[#F5F8FF] p-2 rounded-full ml-2 mr-2"
            ><img :src="fbImg" alt=""
          /></a>
          <div class="max-w-md">
            <div
              class="relative flex items-center w-full h-12 rounded-[64px] bg-[#F5F8FF] overflow-hidden"
            >
              <input
                class="peer h-full w-full outline-none text-sm text-[#1D2D35] pr-2 placeholder:text-[#1D2D35] bg-[#F5F8FF] pl-4"
                type="text"
                id="search"
                placeholder="ძიება"
              />
              <div class="grid place-items-center h-full w-12 text-[#1D2D35]">
                <img :src="searchImg" alt="search Logo" />
              </div>
            </div>
          </div>
        </div>
        <div class="relative">
          <div class="flex min-[1240px]:hidden ml-2">
            <button
              @click="toggleNavbar"
              type="button"
              class="-m-2.5 inline-flex items-center justify-center text-gray-700 bg-[#F5F8FF] p-2 rounded-full ml-2 mr-2"
            >
              <svg
                class="h-6 w-6"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                aria-hidden="true"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"
                />
              </svg>
            </button>
          </div>
        </div>
      </div>
    </nav>
    <div
      v-if="showMobileNavbar"
      class="absolute mt-2 w-full bg-white z-50 top-[100px] flex flex-col min-[1240px]:hidden px-4 md:px-0"
    >
      <ul class="container mx-auto py-5">
        <li
          v-for="(category, index) in categories"
          :key="index"
          class="text-[#657178] text-base font-medium mb-10"
        >
          {{ category }}
        </li>
      </ul>
      <div class="mb-6 container mx-auto">
        <div class="flex md:hidden justify-center">
          <a href="#" class="bg-[#F5F8FF] p-2 rounded-full"
            ><img :src="instaImg" alt=""
          /></a>
          <a href="#" class="bg-[#F5F8FF] p-2 rounded-full ml-2 mr-2"
            ><img :src="fbImg" alt=""
          /></a>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
import logoImg from "@/assets/logo.png";
import searchImg from "@/assets/Search.png";
import instaImg from "@/assets/Instagram.png";
import fbImg from "@/assets/Facebook.png";

export default {
  data() {
    return {
      logoImg: logoImg,
      searchImg: searchImg,
      instaImg: instaImg,
      fbImg: fbImg,
      categories: [
        "პოლიტიკა",
        "საზოგადოება",
        "სამართალი",
        "ბიზნესი & ეკონომიკა",
        "პოლიტიკა",
        "საზოგადოება",
        "სამართალი",
        "ბიზნესი & ეკონომიკა",
        "პოლიტიკა",
      ],
      displayedCategories: [],
      hiddenCategories: [],
      isDropdownVisible: false,
      showMobileNavbar: false,
    };
  },
  mounted() {
    this.updateCategories();
    window.addEventListener("resize", this.updateCategories);
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.updateCategories);
  },
  methods: {
    updateCategories() {
      const navWidth = 470;
      let totalWidth = 0;
      let index = 0;
      for (; index < this.categories.length; index++) {
        totalWidth += this.getTextWidth(this.categories[index]);
        if (totalWidth > navWidth) break;
      }
      this.displayedCategories = this.categories.slice(0, index);
      this.hiddenCategories = this.categories.slice(index);
    },
    getTextWidth(text) {
      const span = document.createElement("span");
      span.textContent = text;
      span.style.visibility = "hidden";
      document.body.appendChild(span);
      const width = span.offsetWidth;
      document.body.removeChild(span);
      return width;
    },
    showDropdown() {
      this.isDropdownVisible = true;
    },
    hideDropdown() {
      this.isDropdownVisible = false;
    },
    toggleNavbar() {
      this.showMobileNavbar = !this.showMobileNavbar;
    },
  },
};
</script>

<style scoped>
.category-item {
  white-space: nowrap;
}
</style>
