<script setup>
import { ref } from "vue";
</script>

<template>
  <main>
    <div v-if="showModal" class="overlay">
      <div class="modal">
        <textarea
          v-model="newNote"
          name="notes"
          id="notes"
          cols="30"
          rows="10"
        ></textarea>
        <button @click="addNote(), changeModal()">Add Note</button>
        <button class="close" @click="changeModal()">Close</button>
      </div>
    </div>
    <div class="container">
      <header>
        <h1>Notes!</h1>
        <button @click="changeModal()">+</button>
      </header>
      <div class="card-container">
        <div :style="{backgroundColor: note.backgroundColor}" v-for="note in notes" class="card" :key="note.id">
          <p class="main-text">
            {{ note.text }}
          </p>
          <p class="date">{{note.date.toLocaleDateString("en-US")}}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;500;700;900&display=swap");

main {
  height: 100vh;
  widows: 100vw;
  font-family: "Roboto", sans-serif;
}

.overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.753);
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}

.container {
  max-width: 1000px;
  padding: 10px;
  margin: 0 auto;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 4em;
}

header button {
  border: none;
  background-color: inherit;
  font-size: 1em;
  background-color: black;
  color: white;
  padding: 0.2em;
  border-radius: 50%;
  width: 2.5em;
  height: 2.5em;
}

button:hover {
  cursor: pointer;
  background-color: rgb(54, 53, 53);
}

h1 {
  font-weight: bold;

  font-size: 5em;
}

.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 1em;
  padding: 1em;
}
.card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 14em;
  font-size: 0.9em;
  height: 17em;
  border-radius: 0.8em;
  padding: 1em;
  background-color: orange;
  line-height: 1.4em;
}

.date {
  font-size: 0.8em;
  font-weight: bolder;
}

.modal {
  border: 1px solid white;
  width: 47em;
  background-color: white;
  border-radius: 0.7em;
  padding: 1em;
  overflow: hidden;
  position: relative;
  display: flex;
  flex-direction: column;
}

.modal button {
  padding: 0.7em 1.2em;
  font-size: 1.1em;
  width: 100%;
  background-color: blueviolet;
  border: none;
  border-radius: 0.6em;
  color: white;
  cursor: pointer;
  margin-top: 1em;
}
.modal .close {
  background-color: red;
  margin-top: 0.6em;
}
</style>

<script>
export default {
  data() {
    return {
      showModal: ref(false),
      newNote: "",
      notes: [],
    };
  },
  methods: {
    changeModal() {
      if (this.showModal == false) {
        this.showModal = true;
      } else {
        this.showModal = false;
      }
    },
    getRandomColor() {
      let color = "hsl(" + Math.random() * 360 + ", 100%, 75%)";
      return color;
    },
    addNote() {
      if(this.newNote != ""){
        this.notes.push({
        id: Math.floor(Math.random() * 10000),
        text: this.newNote,
        date: new Date(),
        backgroundColor: this.getRandomColor(),
      });
      this.newNote = "";
      }
    },
  },
};
</script>
