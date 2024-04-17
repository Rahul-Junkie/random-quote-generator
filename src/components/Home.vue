<template>
  <div
    class="min-h-screen bg-gray-100 py-6 flex flex-col justify-center sm:py-12"
  >
    <p class="mx-auto italic text-xl text-gray-800">Random Quote Generator</p>
    <!-- Quote component  -->
    <Quote :quoteData="quoteData" />
    <!-- Button to Generate quote -->
    <button
      class="relative bg-gray-900 text-white text-center text-xs outline-none uppercase tracking-widest py-3 px-4 leading-4 transition-all duration-500 ease-in-out rounded-full cursor-pointer"
      v-bind:class="{ 'pr-8 pl-4': buttonClicked }"
      v-on:click="buttonClick"
    >
      {{ buttonText }}

      <div
        class="absolute right-4 h-8 w-8 animate-bounce rounded-full"
        v-show="buttonClicked"
      >
        <!-- Adjusted position to 'right-4' -->
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="animate-spin"
          fill="currentColor"
          stroke="currentColor"
          stroke-width="0"
          viewBox="0 0 16 16"
        >
          <path
            d="M8 0c-4.418 0-8 3.582-8 8s3.582 8 8 8 8-3.582 8-8-3.582-8-8-8zM8 4c2.209 0 4 1.791 4 4s-1.791 4-4 4-4-1.791-4-4 1.791-4 4-4zM12.773 12.773c-1.275 1.275-2.97 1.977-4.773 1.977s-3.498-0.702-4.773-1.977-1.977-2.97-1.977-4.773c0-1.803 0.702-3.498 1.977-4.773l1.061 1.061c0 0 0 0 0 0-2.047 2.047-2.047 5.378 0 7.425 0.992 0.992 2.31 1.538 3.712 1.538s2.721-0.546 3.712-1.538c2.047-2.047 2.047-5.378 0-7.425l1.061-1.061c1.275 1.275 1.977 2.97 1.977 4.773s-0.702 3.498-1.977 4.773z"
          ></path>
        </svg>
      </div>
    </button>
  </div>
</template>
<script>
import Quote from "./Quote.vue";
import axios from "axios";
export default {
  name: "Home",
  components: { Quote },
  data() {
    return {
      iconClass: "duration-200 transform hover:scale-105",
      originalbuttonText: "Generate Quote",
      buttonClicked: false,
      quoteData: {
        _id: "27YFtyxa8nBj",
        content: "Meaning is not what you start with but what you end up with.",
        author: "Peter Elbow",
        tags: ["Famous Quotes"],
        authorSlug: "peter-elbow",
        length: 60,
        dateAdded: "2019-08-08",
        dateModified: "2023-04-14",
      },
    };
  },
  created() {
    this.setButtonText();
  },
  methods: {
    buttonClick() {
      this.buttonClicked = true;
      this.buttonText = "Generating...";
      this.fetchRandomQuote();
      setTimeout(() => {
        this.buttonClicked = false;
        this.buttonText = "Done!";
      }, 1000);
    },
    setButtonText() {
      this.buttonText = this.originalbuttonText;
    },
    // Fetch Random Quote
    async fetchRandomQuote() {
      try {
        const response = await axios.get("https://api.quotable.io/random");
        if (response.status === 200) {
          this.quoteData = response.data;
        } else {
          throw new Error("Failed to fetch quote");
        }
      } catch (error) {
        // If there's an error in the request, log the error and return null
        alert("Error fetching quote:", error.message);
      }
    },
  },
};
</script>
