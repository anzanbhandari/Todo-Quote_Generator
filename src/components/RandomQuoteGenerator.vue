<script setup>
import {ref, onMounted} from 'vue'

let qoutes = ref([
    {
        text: 'You are the shuckiest shuck faced shuck in the world!',
        author: 'James Dashner'
    },
    {
        text: 'Her name badge read: Hello! My name is DIE, DEMIGOD SCUM!',
        author: 'Rick Riordan'
    },
    {
        text: 'Insane means fewer cameras!',
        author: 'Ally Carter'
    },
    {
        text: 'I am about as intimidating as a butterfly.',
        author: 'Dan Howell'
    }
])

let currentQuote = ref({text: ' ', author: ''})

let getRandomQuote = ()=> {
    let randomIndex = Math.floor(Math.random() * qoutes.value.length)

    currentQuote.value = qoutes.value[randomIndex]
}

onMounted(getRandomQuote)
</script>

<template>
    <div class="quote-generator">
        <h1 class="app-title">Random Quote Generator</h1>
        <blockquote class="quote-container">
            <p> {{ currentQuote.text }} </p>
            <cite> {{ currentQuote.author }} </cite>
        </blockquote>

        <button @click="getRandomQuote" class="quote-button">It's a Thought</button>

    </div>
</template>

<style scoped>
.quote-generator {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  text-align: center;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.app-title {
  font-size: 24px;
  margin-bottom: 20px;
  color: #333;
}

.quote-container {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 8px;
  border: 1px solid #ddd;
  margin-bottom: 20px;
}

p {
  font-size: 18px;
  margin-bottom: 10px;
}

cite {
  font-style: normal;
  color: #777;
}

.quote-button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #3498db;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.quote-button:hover {
  background-color: #2980b9;
}
</style>