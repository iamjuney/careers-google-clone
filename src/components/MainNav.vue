<template>
  <header class="w-full text-sm">
    <div class="fixed top-0 left-0 h-16 w-full bg-white">
      <div
        class="flex-no-wrap mx-auto flex h-full border-b border-solid border-brand-gray-1 px-8 text-gray-500 shadow-sm"
      >
        <a href="/" class="flex h-full items-center text-2xl">
          {{ company }}
        </a>

        <nav class="ml-12 h-full">
          <ul class="m-0 flex h-full list-none p-0">
            <li
              v-for="menuItem in menuItems"
              :key="menuItem"
              class="ml-9 h-full first:ml-0"
              data-test="main-nav-list-item"
            >
              <a
                href="#"
                class="flex h-full items-center py-2.5 hover:text-gray-900"
              >
                {{ menuItem }}
              </a>
            </li>
          </ul>
        </nav>

        <div class="ml-auto flex h-full items-center">
          <profile-image v-if="isLoggedIn" @click="logout" />
          <action-button v-else text="Sign in" @click="login" />
        </div>
      </div>
    </div>
  </header>
</template>

<script>
import ActionButton from "@/components/ActionButton.vue";
import ProfileImage from "@/components/ProfileImage.vue";

export default {
  name: "MainNav",
  components: {
    ActionButton,
    ProfileImage,
  },
  data() {
    return {
      company: "Google Careers",
      url: "https://careers.google.com",
      menuItems: ["Teams", "Locations", "Benefits", "Jobs", "Students"],
      isLoggedIn: false,
    };
  },
  methods: {
    login() {
      this.isLoggedIn = true;
    },
    logout() {
      this.isLoggedIn = false;
    },
  },
};
</script>
