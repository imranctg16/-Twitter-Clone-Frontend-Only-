<template>
  <div id="app" class="flex container h-screen w-full">
    <!-- nav bar -->
    <div class="w-1/5 border-r border-lighter px-16 py-4">
      <button
        class="h-12 w-12 hover:bg-lightblue text-3xl rounded-full text-blue"
      >
        <i class="fab fa-twitter"></i>
      </button>
      <!-- tabs -->
      <div>
        <button v-for="tab in tabs" class="flex items-center px-2 py-2 rounded-full hover:bg-lightblue hover:text-blue">
          
          <i :class="tab.icon" class="text-2xl mr-4"></i>
          <p class="text-lg font-sans">{{ tab.title }}</p>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  components: {},
  data() {
    return {
      tabs: [
        { icon: "fas fa-home", title: "Home", id: "home" },
        { icon: "fas fa-hashtag", title: "Explore", id: "explore" },
        { icon: "far fa-bell", title: "Notifications", id: "notifications" },
        { icon: "far fa-envelope", title: "Messages", id: "messages" },
        { icon: "far fa-bookmark", title: "Bookmarks", id: "bookmarks" },
        { icon: "fas fa-clipboard-list", title: "Lists", id: "lists" },
        { icon: "far fa-user", title: "Profile", id: "profile" },
        { icon: "fas fa-ellipsis-h", title: "More", id: "more" },
      ],
    };
  },
};
</script>
