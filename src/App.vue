<template>
  <header>
    <nav>
      <div class="logo">
        <img
          src="https://www.sparkfish.com/assets/images/4cac050e9b195cc2fdc1ac6d3c146759-1229.png"
          alt="Sparkfish Logo"
        />
      </div>
      <ul>
        <li><a href=""> Daily Advice</a></li>
        <li><a href=""> Advice Search</a></li>
        <li><a href=""> Random Advice</a></li>
      </ul>
      <!-- // Style the navbar -->
    </nav>
  </header>

  <main>
    <div id="searchBox">
      <input type="text" name="searchBoxQuery" id="searchBoxQuery" />
      <!-- // Style the searchbox -->
    </div>
    <div id="searchResults">
      <ul>
        <li>Search Query: query</li>
        <li>Result Count: results</li>
      </ul>
      <!-- // Add your search results code here -->
      <div>
        <span>Result Advice</span>
        <details>
          <label>Result Publish Date: </label>
          <span>Result Date</span>
        </details>
      </div>
    </div>
  </main>
</template>

<script>
/**
 * Welcome to the Sparkfish Interview process. This Code
 * Challenge is designed to get to know you. We've left it
 * pretty simple and fairly blank. We've done some setup
 * for you to reduce the time you spend on this challenge.
 *
 * Please finish this by integrating properly with the API
 * and handling search results. The navbar contains some extra
 * UI elements you can create for extra credit. Please note they
 * are NOT required.
 *
 * Requirements:
 *    * User can type in serch box and click enter to search for new results
 *    * User can easily read the results
 *    * The UI is clean and modern.
 *    * The UI makes sense and is intiutive.
 *    * UI has a loader
 *    * UI prevents searching without input
 *
 * This challenge really focuses on your front-end skills. But, we
 * do want to make sure you can work with API's with relative ease.
 *
 * Good luck!
 *
 * ~~ The Sparkfish Team
 *
 * @updated 06-01-2022 by Brent
 */
import { ref } from "vue";

const APIBaseUrl = "https://api.adviceslip.com/advice/";

export default {
  setup() {
    let searchQuery = ref("");
    let searchResults = ref({});

    return {
      searchQuery,
      searchResults,
    };
  },
  mounted() {
    this.searchQuery = "People";
    this.search();
  },
  methods: {
    search() {
      fetch(APIBaseUrl + `saerch/${this.searchQuery}`).then(
        (result) => (this.searchResults = result)
      );
    },
  },
};
</script>

<style>
@import "./assets/base.css";

#app {
  max-width: 1920px;
  margin: 0 auto;
  padding: 0;

  font-weight: normal;
}

header {
  line-height: 1.5;
}
</style>
