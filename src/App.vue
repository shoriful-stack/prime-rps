<script setup>
import { ref } from 'vue';

// Choices for the game
const choices = ["Rock", "Paper", "Scissors"];

// define the playerChoice, computerChoice, and result refs
const playerChoice = ref('None');
const computerChoice = ref('None');
const result = ref('');

// Function to play the game when a choice button is clicked
const playGame = (choice) => {
  playerChoice.value = choice;

  // Computer randomly selects
  const randomIndex = Math.floor(Math.random() * choices.length);
  computerChoice.value = choices[randomIndex];

  // Determine winner
  if (playerChoice.value === computerChoice.value) {
    result.value = "It's a Tie!";
  } else if (
    (playerChoice.value === "Rock" && computerChoice.value === "Scissors") ||
    (playerChoice.value === "Scissors" && computerChoice.value === "Paper") ||
    (playerChoice.value === "Paper" && computerChoice.value === "Rock")
  ) {
    result.value = "You Win!";
  } else {
    result.value = "You Lose!";
  }
};
</script>

<template>
  <div>
    <h2>Rock, Paper, Scissors</h2>

    <div>
      <!-- Buttons to choose options (e.g : Rock, Paper, Scissors ) -->
      <button v-for="(choice, index) in choices" :key="index" @click="playGame(choice)">
        {{ choice }}
      </button>
    </div>

    <p>Your Choice :
      <span class="choice-text">
        {{ playerChoice }}
      </span>
    </p>

    <p>Computer's Choice :
      <span class="choice-text">
        {{ computerChoice }}
      </span>
    </p>

    <h3>
      {{ result }}
    </h3>
  </div>
</template>

<style scoped>
button {
  margin: 5px;
}

.choice-text {
  font-weight: bold;
}
</style>
