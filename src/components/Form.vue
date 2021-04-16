<template>
  <form @submit.prevent = "FormHandler">
    <input type="text" placeholder="Description..." v-model="formData.desc">
    <input type="number" placeholder="Value..." v-model="formData.value">
    <input type="date" placeholder="Date..." v-model="formData.date">
    <input type="submit" placeholder="SUBMIT">
  </form>
</template>
<script>
import { reactive } from 'vue'

export default {
  props: {
    state: Object
  },
  setup(props, { emit }) {
    const formData = reactive({
      desc: null,
      value: null,
      date: null
    });
    function FormHandler() {
      emit("add-income", {
        desc: formData.desc,
        value: formData.value,
        date: formData.date
      });
      formData.desc = null,
      formData.value = null,
      formData.date = null
    }
    
    return {
      formData,
      FormHandler
    }
  }
}
</script>
<style scoped>
  form {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    margin-top: 30px;
    margin-bottom: 30px;
    padding: 0 15px;
  }
  form input {
    color: #888;
    border: none;
    outline: none;
    font-size: 20px;
    margin-bottom: 10px;
  }
  form input::placeholder {
    color: #aaa;
  }
  form input:not([type="submit"]) {
    display: block;
    background-color: #fff;
    border: none;
    outline: none;
    padding: 5px 15px;
  }
  form input[type="submit"] {
    display: block;
    background-color: none;
    border: none;
    outline: none;
    color: #fff;
    font-weight: 500;
    text-shadow: 0px 1px 3px rgba(0,0,0,.2);
    padding: 5px 15px;
    background-color: #2a2dff;
    cursor: pointer;
  }
  form input:last-of-type {
    border-radius: 8px 8px 8px 8px;
  }
  
  @media (max-width: 992px) {
    form {
      flex-direction: column;
    }
  }
</style>