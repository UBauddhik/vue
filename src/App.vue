<template>
  <div class="all">
      <button @click="cloneCard">Clone</button>
      <button @click="backgroundColor">Background Color</button>
      <button @click="changeText">Change Text</button>
      <button @click="deleteLastCard">Delete Last Card</button>
      <div class="card" v-for="(card, index) in cards" :key="index">
          <img :src="card.image" >
          <h1>{{ card.title }}</h1>
          <p v-show="card.showDescription">{{ card.description }}</p>
          <button @click="description(index)">Details</button>
      </div>
  </div>
</template>

<script>
export default {
  data() {
      return {
          cards: [{
              image: 'https://www.dalycollege.org/images/slider-1.jpg',
              title: 'Card',
              description: 'The Daly College is a group of institutions in Indore, India that includes a co-educational boarding school, a junior school, an undergraduate management school, and a postgraduate business school.',
              showDescription: false
          }]
      }
  },
  methods: {
      cloneCard() {
          this.cards.push({ ...this.cards[0] });
      },
      backgroundColor() {
          this.$el.querySelector('.card').classList.toggle('light-mode');
          this.$el.querySelector('.card').classList.toggle('dark-mode');
      },
      changeText() {
          this.cards[0].title = "Something Else";
      },
      deleteLastCard() {
          if (this.cards.length > 1) {
              this.cards.pop();
          }
      },
      description(index) {
          this.cards[index].showDescription = !this.cards[index].showDescription;
      }
  }
}
</script>

<style scoped>
  .card {
    display: inline-block;
    max-width: 400px;
    margin: 0 auto;
    text-align: center;
    padding: 16px;
    border: 1px solid #ccc;
    border-radius: 8px;
}

.card img {
    max-width: 100%;
    height: auto;
    width: 100%;
    max-height: 200px;
}

.btn-wrapper {
    margin-top: 16px;
}

.btn-wrapper button {
    background-color: #0074D9;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover,
button:focus {
    background-color: #0056b3;
}

.hidden {
    display: none;
}

.light-mode {
    background-color: #ffffff;
    color: #000000;
}

.dark-mode {
    background-color: #000000;
    color: #ffffff;
}

@media (max-width: 800px) {
    .btn-wrapper button {
        display: none;
    }
}
</style>
