<template>
  <form id="average" @submit.prevent="handleSubmit">
    <label for="date">日期</label>
    <input type="text" id="date" name="date" v-model="formData.date">
    <label for="name">商品名稱</label>
    <input type="text" id="name" name="name" v-model="formData.name">
    <label for="price">商品價格</label>
    <input type="text" id="price" name="price" v-model="formData.price">

    <button type="submit">送出</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        date: '',
        name: '',
        price: ''
      }
    };
  },
  methods: {
    async handleSubmit() {
      const jsonString = JSON.stringify(this.formData);
      console.log(jsonString);

      const url = "http://localhost:3000/api";
      try {
        const response = await fetch(url, {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json'
          },
          body: jsonString,
        });
        const data = await response;
        console.log("成功", data);
      } catch (error) {
        console.log("錯誤", error);
      }
    }
  }
};
</script>

<style scoped>
button {
  background-color: rgb(66, 96, 216);
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  padding: 10px 40px;
}

</style>
