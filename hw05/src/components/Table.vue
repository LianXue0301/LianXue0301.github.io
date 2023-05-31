<template>
  <div>
    <button @click="handleClick">顯示資料</button>
    <table>
      <thead>
      <tr>
        <th>date</th>
        <th>name</th>
        <th>price</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="item in data" :key="item.date">
        <td>{{ item.date }}</td>
        <td>{{ item.name }}</td>
        <td>{{ item.price }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: []
    };
  },
  methods: {
    async handleClick() {
      const url = "http://localhost:3000/api";
      try {
        const response = await fetch(url, {
          method: 'GET',
        });
        const res_data = await response.json();
        this.data = res_data;
        console.log("成功", res_data);
      } catch (error) {
        console.log("錯誤", error);
      }
    }
  }
};
</script>

<style scoped>

table {
  width: 75%;
}

th, td {
  border: 1px solid #000000;
  padding: 10px;
}

th {
  background-color: #af874c;
  color: white;
}
</style>