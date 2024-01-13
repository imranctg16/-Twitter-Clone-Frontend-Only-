<template>
  <div id="app" class="flex container h-screen w-full">
    <!-- nav bar -->
    <div class="lg:w-1/4 border-r border-lighter  px -2 lg:px-16 py-4 flex flex-col justify-between">
      <div>
        <button
          class="h-12 w-12 hover:bg-lightblue text-3xl rounded-full text-blue"
        >
          <i class="fab fa-twitter"></i>
        </button>
        <!-- tabs -->
        <div>
          <button
            v-for="tab in tabs"
            :class="id == tab.id ? 'text-blue' : ''"
            @click="id = tab.id"
            class="flex hover:outline-none items-center px-2 py-2 rounded-full hover:bg-lightblue hover:text-blue mb-3"
          >
            <i :class="tab.icon" class="text-2xl mr-4 text-left"></i>
            <p class="hidden lg:block text-lg font-sans text-left">{{ tab.title }}</p>
          </button>
        </div>
        <!-- tweet button -->
        <button
          class="text-white bg-blue font-bold rounded-full w-12 h-12 lg:h-auto lg:w-full p-3 text-center hover:outline-none hover:bg-darkblue"
        >
          <p class="hidden lg:block"> Tweet</p>
          <i class="fas fa-plus lg:hidden"></i>
        </button>
      </div>
      <!-- profile section -->
      <div class="lg:w-ful relative">
        <button @click="dropdown = true" class="flex items-center w-full hover:bg-lightest rounded-full bg-white">
          <img src="profile.png" class="w-12 h-12 rounded-full border border-lighter">
          <div class="ml-4">
            <p class="text-small font-bold">Imran</p>
             <p class="text-small ">@imran</p>
          </div>
          <i class="fa fa-angle-down ml-auto text-lg"></i>
        </button>
        <!-- dropdown options -->
        <div v-if="dropdown == true" class="absolute bottom-0 left-0 w-64 rounded-lg shadow-md border-lightest bg-white mb-16 ml-14">
          <button  @click="dropdown = false" class="flex items-center w-full hover:bg-lightest rounded-full bg-white">
              <img src="profile.png" class="w-12 h-12 rounded-full border border-lighter">
              <div class="ml-4">
                <p class="text-small font-bold">Imran</p>
                <p class="text-small ">@imran</p>
              </div>
              <i class="fa fa-check  ml-auto text-lg text-blue"></i>
          </button>
          <button @click="dropdown = false" class="w-full text-left hover:bg-lightest border-t border-lighter text-sm">
              Add an existing account
          </button> 
          <button @click="dropdown = false" class="w-full text-left hover:bg-lightest border-t border-lighter text-sm">
              Logout
          </button>
        </div>
      </div>
    </div>
    <!-- tweet section -->
    <div class="w-1/2 h-full">
    </div>
    <!-- trending section -->
    <div class="md:block hidden w-1/3 border-l border-lighter px-6 py-2  overflow-y-scroll relative">
      <input class="pl-12  text-sm rounded-full bg-lighter p-2 w-full" placeholder="search" type="text">
      <i class="fas fa-search absolute top-0 left-0 mt-5 ml-12 text-sm text-light"></i>
      <!-- trends -->
      <div class="w-full bg-lightest rounded-lg">
        <div class="flex items-center justify-between p-3">
          <p class="text-lg font-bold"> Trends for you</p>
          <i class="fas fa-cog text-lg text-blue"></i>
        </div>
        <button v-for="trend in trending" class="w-full flex justify-between hover:bg-lighter p-3 border-t border-lighter">
          <div>
            <p class="text-sm text-left leading-tight">{{ trend.top }} </p>
            <p class="font-bold text-left leading-tight">{{ trend.title }} </p>
            <p class="text-sm text-left leading-tight text-dark">{{  trend.bottom }} </p>
          </div>
          <i class="fas fa-angle-down text-lg text-dark"></i>
        </button>
        <button class="p-3 w-full hover:bg-lighter text-left text-blue border-t border-lighter">
          Show more
        </button>
      </div>
      <!-- who to follow -->
      <div class="w-full bg-lightest rounded-lg my-4">
        <div class="p-3">
          <p class="text-lg font-bold"> Who to follow</p>
        </div>
        <button v-for="friend in friends" class="w-full flex justify-between hover:bg-lighter p-3 border-t border-lighter">
          <img :src="friend.src" class="w-12 h-12 rounded-full border border-lighter">
          <div class="ml-4">
            <p class="text-small font-bold">{{ friend.name }}</p>
             <p class="text-small ">{{ friend.handle }}</p>
          </div>
          <button class="text-sm py-2 text-blue px-4 rounded-full border-2 border-blue">Follow</button>
        </button>
        <button class="p-3 w-full hover:bg-lighter text-left text-blue border-t border-lighter">
          Show more
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
      id: 'home',
      dropdown:false,
      trending: [
        {top: 'Trending in TX', title: 'Gigi', bottom: 'Trending with: Rip Gigi'},
        {top: 'Music', title: 'We Won', bottom: '135K Tweets'},
        {top: 'Pop', title: 'Blue Ivy', bottom: '40k tweets'},
        {top: 'Trending in US', title: 'Denim Day', bottom: '40k tweets'},
        {top: 'Trending', title: 'When Beyonce', bottom: '25.4k tweets'},
      ],
      friends: [
        {src: 'elon.jpg', name: 'Elon Musk', handle: '@teslaBoy'},
        {src: 'monk.jpg', name: 'Adrian Monk', handle: '@detective:)'},
        {src: 'kevin.jpg', name: 'Kevin Hart', handle: '@miniRock'}
      ],
    };
  },
};
</script>
