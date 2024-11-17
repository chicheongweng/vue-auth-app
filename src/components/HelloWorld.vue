<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      Welcome to our ESG (Environmental, Social, and Governance) platform. Here, we are committed to providing transparent and comprehensive ESG data.
    </p>
    <h3>Our ESG Focus Areas</h3>
    <ul>
      <li>Environmental Sustainability</li>
      <li>Social Responsibility</li>
      <li>Governance and Ethics</li>
    </ul>
    <h3>Key Metrics</h3>
    <ul>
      <li>Carbon Emissions</li>
      <li>Water Usage</li>
      <li>Employee Satisfaction</li>
      <li>Community Engagement</li>
      <li>Board Diversity</li>
      <li>Ethical Compliance</li>
    </ul>
    <h3>Learn More</h3>
    <ul>
      <li><a href="https://www.un.org/sustainabledevelopment/sustainable-development-goals/" target="_blank" rel="noopener">UN Sustainable Development Goals</a></li>
      <li><a href="https://www.globalreporting.org/" target="_blank" rel="noopener">Global Reporting Initiative</a></li>
      <li><a href="https://www.sasb.org/" target="_blank" rel="noopener">SASB Standards</a></li>
      <li><a href="https://www.cdp.net/en" target="_blank" rel="noopener">CDP</a></li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: {
      type: String,
      required: true
    }
  }
});
</script>

<style scoped>
.hello {
  padding: 20px;
}

h1 {
  color: #42b983;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 5px 0;
}

a {
  color: #42b983;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}
</style>