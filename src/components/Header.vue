<template>
  <header>
    <h1>Income Tracker</h1>
    <div class="total-income">${{totalIncome}}</div>
  </header>
</template>

<script>
export default {
  props: {
    totalIncome: Number
  }
}
</script>

<style scoped>
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px 30px;
    background-color: #2a2dff;
    border-bottom: 5px solid rgb(155, 155, 155);
  }
  header h1 {
    color: #eee;
    font-size: 28px;
  }
  header .total-income {
    background-color: #8d8d8d;
    color: #fff;
    font-size: 20px;
    font-weight: 900;
    padding: 5px 10px;
    min-width: 100px;
    right: auto;
    text-align: center;
    border-radius: 8px;
    box-shadow: inset 0px 0px 6px rgba(0,0,0,.25);
    text-shadow: 0px 3px 3px rgba(0,0,0,.25);
  }
</style>