<template lang="">
     <div class="bg-transparent fixed w-full nav"  :class="{ 'scrolled': !view.atTopOfPage }" >
    <div
      class="px-4 py-5 mx-auto  sm:max-w-xl
          md:max-w-screen-2xl
          lg:max-w-screen-lg 2xl:max-w-screen-xl md:px-16 lg:px-28 xl:px-0"
    >
      <div class="relative flex items-center justify-between">
        <a
          href="/"
          aria-label="Company"
          title="Company"
          class="inline-flex items-center"
        >
         <img src ="../assets/logo.png" class="w-auto h-10" />
        </a>
        <ul class="flex items-center hidden space-x-12 justify-end lg:flex ">
          <li >
            <a
           :class="[view.atTopOfPage ? 'text-white' : 'text-black']"
              href="/"
              aria-label="Product pricing"
              title="Product pricing"
              class="font-medium text-right tracking-wide transition-colors duration-200 hover:text-teal-accent-400"
              >About Us</a
            >
          </li>
          <li >
            <a
              :class="[view.atTopOfPage ? 'text-white' : 'text-black']"
              href="/"
              aria-label="About us"
              title="About us"
              class="font-medium tracking-wide transition-colors duration-200 hover:text-teal-accent-400"
              >Contact us</a
            >
          </li>
        </ul>
        <ul class="flex items-center hidden space-x-8 lg:flex">
          <li>
              <router-link to="/register">
              <a href=''>
            <button
              :class="[view.atTopOfPage ? 'bgNotScrolled'  : 'bgScrolled']"
            
              class="inline-flex items-center justify-center h-12 px-6 font-medium tracking-wide  btn transition duration-200 rounded-2xl shadow-md bg-deep-purple-accent-400 hover:bg-deep-purple-accent-700 focus:shadow-outline focus:outline-none"
              aria-label="Sign up"
              title="Sign up"
            >
            Download
            </button>
            </a>
            
            </router-link>
          </li>
        </ul>
        <div class="lg:hidden">
          <button
            aria-label="Open Menu"
            title="Open Menu"
            class="p-2  bg-white -mr-1 transition duration-200 rounded focus:outline-none focus:shadow-outline"
            @click="isMenuOpen = true"
          >
            <svg class="w-5 text-gray-600" viewBox="0 0 24 24">
              <path
                fill="currentColor"
                d="M23,13H1c-0.6,0-1-0.4-1-1s0.4-1,1-1h22c0.6,0,1,0.4,1,1S23.6,13,23,13z"
              ></path>
              <path
                fill="currentColor"
                d="M23,6H1C0.4,6,0,5.6,0,5s0.4-1,1-1h22c0.6,0,1,0.4,1,1S23.6,6,23,6z"
              ></path>
              <path
                fill="currentColor"
                d="M23,20H1c-0.6,0-1-0.4-1-1s0.4-1,1-1h22c0.6,0,1,0.4,1,1S23.6,20,23,20z"
              ></path>
            </svg>
          </button>
          <div v-if="isMenuOpen" class="absolute top-0 left-0 w-full">
            <div class="p-5 bg-white border rounded shadow-sm">
              <div class="flex items-center justify-between mb-4">
              
                <div>
                  <button
                    aria-label="Close Menu"
                    title="Close Menu"
                    class="p-2 -mt-2 -mr-2 transition duration-200 rounded hover:bg-gray-200 focus:bg-gray-200 focus:outline-none focus:shadow-outline"
                    @click="isMenuOpen = false"
                  >
                    <svg class="w-5 text-gray-600" viewBox="0 0 24 24">
                      <path
                        fill="currentColor"
                        d="M19.7,4.3c-0.4-0.4-1-0.4-1.4,0L12,10.6L5.7,4.3c-0.4-0.4-1-0.4-1.4,0s-0.4,1,0,1.4l6.3,6.3l-6.3,6.3 c-0.4,0.4-0.4,1,0,1.4C4.5,19.9,4.7,20,5,20s0.5-0.1,0.7-0.3l6.3-6.3l6.3,6.3c0.2,0.2,0.5,0.3,0.7,0.3s0.5-0.1,0.7-0.3 c0.4-0.4,0.4-1,0-1.4L13.4,12l6.3-6.3C20.1,5.3,20.1,4.7,19.7,4.3z"
                      ></path>
                    </svg>
                  </button>
                </div>
              </div>
              <nav>
                <ul class="space-y-6 text-center ">
                
                  <li>
                    <a
                      href="/"
                      aria-label="Contact Us"
                      title="Contact Us"
                      class="font-medium tracking-wide text-gray-700 transition-colors duration-200 hover:text-deep-purple-accent-400"
                      >About Us</a
                    >
                  </li>
                  <li>
                    <a
                      href="/"
                      aria-label="About us"
                      title="About us"
                      class="font-medium tracking-wide text-gray-700 transition-colors duration-200 hover:text-deep-purple-accent-400"
                      >Contact us</a
                    >
                  </li>
                  <!-- <li>
                    <a
                      href="/"
                      class="inline-flex items-center justify-center w-full h-12 px-6 font-medium tracking-wide text-white transition duration-200 rounded shadow-md bg-deep-purple-accent-400 hover:bg-deep-purple-accent-700 focus:shadow-outline focus:outline-none"
                      aria-label="Sign up"
                      title="Sign up"
                    >
                      Get Started
                    </a>
                  </li> -->
                </ul>
              </nav>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Navbar",

  data() {
    return {
      isMenuOpen: false,
      view: {
        atTopOfPage: true,
      },
    };
  },

  beforeMount() {
    window.addEventListener("scroll", this.handleScroll);
  },

  methods: {
    // the function to call when the user scrolls, added as a method
    handleScroll() {
      // when the user scrolls, check the pageYOffset
      if (window.pageYOffset > 0) {
        // user is scrolled
        if (this.view.atTopOfPage) this.view.atTopOfPage = false;
      } else {
        // user is at top of page
        if (!this.view.atTopOfPage) this.view.atTopOfPage = true;
      }
    },
  },
};
</script>