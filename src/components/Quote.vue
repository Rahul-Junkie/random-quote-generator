<template>
  <div class="relative py-3 sm:max-w-3xl sm:mx-auto group card">
    <!-- Quotes -->
    <svg
      class="absolute transform -left-12 -top-12"
      width="100"
      height="78"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <path
        fill-rule="evenodd"
        clip-rule="evenodd"
        d="M100 0H86.588L59.034 40.478v37.065h37.064V40.478H82.2L100 0zM40.966 0H27.554L0 40.478v37.065h37.064V40.478H23.165L40.965 0z"
        fill="#871EFF"
      />
    </svg>
    <svg
      class="absolute transform -right-12 -bottom-6 flip"
      width="101"
      height="78"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <path
        d="M14.2916 77.9999H0.880127L18.6808 37.5217H4.78164V0.457275H41.846V37.5217L14.2916 77.9999Z"
        fill="#871EFF"
      />
      <path
        d="M73.4115 78H60L77.8007 37.5218H63.9015V0.457397H100.966V37.5219L73.4115 78Z"
        fill="#871EFF"
      />
    </svg>
    <!-- Card -->
    <div class="flex flex-row relative bg-white shadow-xl">
      <div
        class="border-gray-800 border-8 bg-center w-full h-72 bg-no-repeat bg-center bg-cover"
        style="background-image: url(https://e7.pngegg.com/pngimages/983/641/png-clipart-bill-gates-quotes-bill-gates-quotes-quotations-famous-quotes-quotation-marks-in-english-sentence-quotation-angle-text.png)"
      >
      </div>
      <div
        class="relative px-4 py-6 sm:p-10 w-3/2 flex flex-wrap content-center"
      >
        <div class="space-y-3">
          <p class="italic text-xl text-gray-800">
           {{quoteData.content}}
          </p>
          <div class="space-y-0">
            <p class="text-xl text-purple-500">{{quoteData.author}}</p>
            <p class="text-base text-gray-500">{{quoteData.dateAdded}}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ["quoteData"],
};
</script>