<template>
    <div class="mainWrapper">
        <h3>Screening Test</h3>
  <div>
    <ul>
      <li v-for="(input, index) in inputArray" :key="index">
        {{ input }}
      </li>
    </ul>
    <button @click="findMatchingPairs">Find Matching Pairs</button>
  </div>
  <div v-if="matchingPairs && matchingPairs.length">
      <h3>Matching Pairs:</h3>
      <ul>
        <li v-for="(pair, index) in matchingPairs" :key="index">
          {{ pair }}
        </li>
      </ul>
    </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      inputArray: ["2kg", "6kgg", "8kg", "10kg", "2kg", "2kg", "6kg", "6kg", "6kg"],
    };
  },
  methods: {
    findMatchingPairs() {
      const inputCounts = {};
      const matchingPairs = [];

      for (let i = 0; i < this.inputArray.length; i++) {
        const input = this.inputArray[i];

        if (inputCounts[input]) {
          inputCounts[input]++;
          if (inputCounts[input] === 2) {
            matchingPairs.push(input);
          }
        } else {
          inputCounts[input] = 1;
        }
      }

      console.log("Matching pairs:", matchingPairs);
    },
  },
};
</script>

<style lang="scss"></style>