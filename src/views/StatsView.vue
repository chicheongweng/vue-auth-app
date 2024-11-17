<template>
  <div class="stats">
    <h1>ESG Statistics</h1>
    <button @click="logout">Logout</button>
    <table>
      <thead>
        <tr>
          <th>Category</th>
          <th>Metric</th>
          <th>Value</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Environmental</td>
          <td>Carbon Emissions</td>
          <td>1200 tons</td>
        </tr>
        <tr>
          <td>Environmental</td>
          <td>Water Usage</td>
          <td>5000 m³</td>
        </tr>
        <tr>
          <td>Social</td>
          <td>Employee Satisfaction</td>
          <td>85%</td>
        </tr>
        <tr>
          <td>Social</td>
          <td>Community Engagement</td>
          <td>70%</td>
        </tr>
        <tr>
          <td>Governance</td>
          <td>Board Diversity</td>
          <td>40%</td>
        </tr>
        <tr>
          <td>Governance</td>
          <td>Ethical Compliance</td>
          <td>95%</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { useRouter } from 'vue-router';

export default defineComponent({
  name: 'StatsView',
  setup() {
    const router = useRouter();

    const logout = () => {
      router.push('/logout');
    };

    return {
      logout,
    };
  },
});
</script>

<style scoped>
.stats {
  padding: 20px;
}

button {
  margin-bottom: 20px;
  padding: 10px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #369f6e;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  border: 1px solid #ddd;
  padding: 8px;
}

th {
  background-color: #f2f2f2;
  text-align: left;
}
</style>