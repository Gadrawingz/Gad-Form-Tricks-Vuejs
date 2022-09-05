<template>
  <div class="container">
    <div class="column border-none">
      <form>
        <label>Email: </label>
        <input type="email" v-model="email" required>

        <label>Password: </label>
        <input type="password" v-model="password" required>
      </form>
    </div>

    <div class="column">
      <div class="showin">
        <p><mark>Email: </mark> {{ email }}</p>
        <p><mark>Password: </mark> {{ password }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

.container {
  background: #ecf;
  border-radius: 5px;
  padding: 10px;
  display: flex;
  flex-direction: row;
}

.container .column {
  display: flex;
  align-items: left;
  justify-content: left;
  border-left: 5px solid brown;
  margin: 4px;
  flex: 2;
}


form, .showin {
  width: 100%;
  margin: 30px auto;
  background: #FFF;
  text-align: left;
  padding: 35px;
  border-radius: 8px;
}

.showin {
  margin-left: 8px!important;
  font-family: Candara;
}

label {
  color: lightseagreen;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.9em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}

input {
  display: block;
  padding: 12px 8px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-left: 1px solid blue;
  border-bottom: 1px solid blue;
  border-radius: 3px;
  color: #555DEF;
}

.border-none {
  border: none!important;
}


</style>
