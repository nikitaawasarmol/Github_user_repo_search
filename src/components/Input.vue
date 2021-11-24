<template>
  <header>
    <form @submit.prevent="event => $emit('input', nameData)">
      <h1>Search github profile here</h1>
      <div class="input-container">
        <input type="text" v-model="nameData" placeholder="Search or jump to..." />
      </div>
      <div class="positionBtn">
        <button type="submit" class="btnSearch">Search</button>
      </div>
    </form>
  </header>
</template>

<script>
export default {
  name: 'Input',
   data() {
      return {
        nameData: ''
      }
    }
}
</script>

<style scoped>
.btnSearch {
  margin-top: 20px;
  width: 120px;
  height: 40px;
  font-size: 1.2rem;
  background-color: #f6f8fa;
  width: 100%;
  border: none;
  border-radius: 30px;
  color: #484f59;
  cursor: pointer;
}
header {
  width: 80%;
}
.btnsearch:hover {
  background-color: #484f59;
}
.positionBtn {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* .input-container {
  position: relative;
} */

label {
  top: 0;
  left: 0;
  right: 0;
  color: #616161;
  display: flex;
  align-items: center;
  position: absolute;
  font-size: 1rem;
  cursor: text;
  transition: 0.2s ease-in-out;
  box-sizing: border-box;
}
/* .input-container {
  position: relative;
} */
input {
  border: 1px solid rgb(80, 79, 79);
  border-radius: 9px;
  outline: none;
  padding-left: 20px;
  transition: 0.2s ease-in-out;
  box-sizing: border-box;
  background-color: #24292F;
  color: rgb(230, 227, 227);
}
input{
  width: 100%;
  height: 3rem;
  font-size: 1rem;
  font-weight: 500;
}


h1 {
  color: #616161;
  text-align: center;
  margin-bottom: 30px;
}

header {
  margin: 15px;
  box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.14), 0 1px 5px 0 rgba(0, 0, 0, 0.12),
    0 3px 1px -2px rgba(0, 0, 0, 0.2);
  padding: 20px;
  border-radius: 0 0 2px 2px;
  background-color: #24292F;
}

</style>
