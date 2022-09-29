<template>
  <div class="container">
    <div class="column border-none">
      <form @submit.prevent="handleSubmit()">
        <label>Email: </label>
        <input type="email" v-model="email" required>

        <label>Password: </label>
        <input type="password" v-model="password" required>
        <div class="error" v-if="passwordError"> {{ passwordError }} </div>

        <label>Job Title: </label>
        <select v-model="job_title" required>
          <option value="Web Developer">Web Developer</option>
          <option value="Web Designer">Web Designer</option>
          <option value="Game Developer">Game Developer</option>
          <option value="Android Developer">Android Developer</option>
        </select>

        <div class="">
          <label>Favorite sports: </label><br>
          <input type="checkbox" v-model="sports" id="basketball" value="Basketball">
          <label for="basketball" class="not-label">Basketball</label>&nbsp;&nbsp;
          <input type="checkbox" v-model="sports" id="football" value="Football">
          <label for="football" class="not-label">Football</label>&nbsp;&nbsp;
          <input type="checkbox" v-model="sports" id="volleyball" value="Volleyball">
          <label for="volleyball" class="not-label">Volleyball</label>&nbsp;&nbsp;
          <input type="checkbox" v-model="sports" id="acrobatics" value="Acrobatics">
          <label for="acrobatics" class="not-label">Acrobatics</label>
        </div>

        <label>Add skills (then press alt+comma): </label>
        <input type="text" v-model="tempSkill" @keyup.alt="addSkill">
        <div class="pill" v-for="skill in skills" :key="skill">
          <span @click="removeSkill(skill)"> {{ skill }} </span>
        </div>

        <div class="">
          <input type="checkbox" class="terms-check" v-model="terms" id="terms">
          <label for="terms" class="not-label">Accept terms and conditions before proceeding</label>
        </div>

        <div class="button">
          <button>Create Account</button>
        </div>

      </form>
    </div>

    <div class="column">
      <div class="showin">
        <h2 class="hr">Output Side</h2>
        <p><mark>Email: </mark> {{ email }}</p>
        <p><mark>Password: </mark> {{ password }}</p>
        <p><mark>Job title: </mark> {{ job_title }}</p>
        <p><mark>Terms accepted: </mark> {{ terms }}</p>
        <p><mark>Selected sports: </mark> {{ sports }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      job_title: '',
      terms: false,
      sports: [],
      tempSkill: '',
      skills: [],
      passwordError: ''
    }
  },
  methods: {
    addSkill(e){
      // If it has comma and skill is not empty 
      if(e.key===',' && this.tempSkill) {
        // Avoid duplication of skills
        if(!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill)
        }
        this.tempSkill = ''
      }
    },
    removeSkill(skill) {
      this.skills = this.skills.filter((item) => {
        return skill !== item
      })
    },
    handleSubmit() {
      // Make Password Validation
      this.passwordError = this.password.length > 5 ?
      '' : 'Password has to be at least 5 chars long' 
      
      if(!this.passwordError) {
        console.log("Email: ", this.email)
        console.log("Password: ", this.password)
        console.log("Job title: ", this.job_title)
        console.log("Sports: ", this.sports)
        console.log("Skills: ", this.skills)
        console.log("Terms n Conditins: ", this.terms)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

.container {
  display: flex;
  flex-direction: row;
}

.container .column {
  display: flex;
  align-items: left;
  justify-content: left;
  border-left: 4px dotted blue;
  margin: 4px;
  flex: 2;
}


form, .showin {
  width: 100%;
  padding-top: 0!important;
  background: #EEE;
  text-align: left;
  padding: 35px;
  border-left: 2px solid rgb(38, 84, 107);
}

.showin {
  margin-left: 8px!important;
  font-family: Candara;
}

label {
  color: lightseagreen;
  display: inline-block;
  margin: 15px 0 10px;
  font-size: 0.9em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}

input, select {
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

input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}

select {
  border: 1px blue solid;
  border-top: none;
}

.border-none {
  border: none!important;
}

.not-label {
  color: black!important;
  text-transform: capitalize!important;
}

mark {
  border-bottom: 2px solid green;
  padding: 4px;
  background: none;
  font-family: Cambria;
  font-weight: bold;
  margin-right: 8px;
}

.hr {
  border-bottom: 2px solid #000;
  padding-top: 5px;
  margin-bottom: 5px;
}

.pill {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background: #000;
  border-radius: 8px;
  font-size: 14px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #FFF;
  font-family: Candara;
  cursor: pointer;
}

.submit {
  text-align: center;
}
button {
  background: blue;
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: #FFF;
  border-radius: 15px;
  font-size: 16px;
}

.error {
  color: #FF0066;
  margin-top: 5px;
  font-size: 0.9em;
  font-weight: bolder;
}

</style>
