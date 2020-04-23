<template>
  <div class="page">
    <div class="intro">
      <img class="logo" :src="logo">
      <h1 class="intro-text">
        <p
          v-for="(line, index) in intro"
          :key="index"
          v-text="line"
        />
      </h1>
    </div>

    <div>
      <template v-for="(component, index) in components">
        <div
          v-if="component.type === 'component_1'"
          :key="index"
          class="component component--1"
        >
          <img :src="component.image">
          <h2>{{ component.headline }}</h2>
          <p>{{ component.description }}</p>
        </div>

        <div
          v-if="component.type === 'component_2'"
          :key="index"
          class="component component--2"
        >
          <div>
            <template v-for="(subcomponent, subindex) in component.subcomponents">
              <div
                v-if="subcomponent.type === 'quote'"
                :key="subindex"
              >
                <blockquote>
                  <p>{{ subcomponent.quote}}</p>
                  <footer>{{ subcomponent.source}}</footer>
                </blockquote>
                <a :href="subcomponent.cta_url">{{ subcomponent.cta_label}}</a>
              </div>
              <div
                v-if="subcomponent.type === 'stat'"
                :key="subindex"
              >
                <img :src="subcomponent.icon">
                <p>{{ subcomponent.number }}</p>
                <p>{{ subcomponent.description }}</p>
              </div>
            </template>
          </div>
          <img :src="component.image">
        </div>
        <div
          v-if="component.type === 'component_3'"
          :key="index"
          class="component component--3"
        >
          <h2>{{ component.headline }}</h2>
          <p>{{ component.description }}</p>
          <ul class="cards">
            <li
              v-for="(card, index) in component.cards"
              :key="index"
              class="card"
            >
              <img :src="card.icon">
              <div v-html="card.description"/>
            </li>
          </ul>
        </div>
      </template>
    </div>
  </div>
</template>

<script>
const home = require('~/data/pages/home.json')

export default {
  data () {
    return home
  },
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  }
}
</script>

<style scoped>
.page {
  padding: 0 1rem;
  max-width: 1000px;
  margin: 0 auto;
}
.intro {
  background-image: linear-gradient(180deg,#071d49,#1ac9a8);
}
.intro-text {
  color: white;
}
.component {
  margin: 2rem 0;
  border: 1px solid blue;
}

.component--1 {
  background-color: black;
  color: white;
}

.component--2 {
  background-color: #ebebeb;
}

.component--3 {
  background-image: linear-gradient(180deg,#071d49,#1ac9a8);
  color: white;
}

.cards {
  display: flex;
  list-style-type: none;
  margin: 0;
  padding: 0.5rem;
}

.card {
  background-color: white;
  color: black;
  margin-right: .5rem;
}

</style>