<template>
    <form @submit.prevent="handlesubmit">
      <label>Email:</label>
      <input type="email" required v-model="email">
  
      <label>Password:</label>
      <input type="password" required v-model="password">
      <div v-if="passwordError" class="error">{{ passwordError }}</div>
  
      <label>Role:</label>
      <select v-model="role">
        <option value="developer">Web Developer</option>
        <option value="designer">Web Designer</option>
        <option value="data-analyst">Data Analyst</option>
      </select>
  
      <label>Skills</label>
      <input type="text" v-model="tempskill" @keyup="addskill">
      <div v-for="skill in skills" :key="skill" class="pill">
        <span @click="deleteskill(skill)">{{ skill }}</span> 
      </div>
  
      <div class="terms">
        <input type="checkbox" v-model="terms" required>
        <label>Accept terms and conditions</label>
      </div>
  
      <div class="submit">
        <button>Create an Account</button>
      </div>
    </form>
    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Skills: {{ skills.join(', ') }}</p>
    <p>Terms Accepted: {{ terms }}</p>
  </template>
   
  <script>
  export default {
    data() {
      return {
        email: '',
        password: '',
        role: '',
        terms: false,
        tempskill: '',
        skills: [],
        passwordError: ''
      }
    },
    methods: {
      addskill(e) {
        if (e.key === ',' && this.tempskill) {
          if (!this.skills.includes(this.tempskill)) {
            this.skills.push(this.tempskill);
          }
          this.tempskill = '';
        }
      },
      deleteskill(skill) {
        this.skills = this.skills.filter(s => s !== skill);
      },
      handlesubmit() {
        this.passwordError = this.password.length >= 6 ? '' : 'Password must be at least 6 characters long';
        if (!this.passwordError) {
          console.log('Form submitted');
          // Add additional form submission logic here
        }
      }
    }
  }
  </script>
  
  <style scoped>
  form {
    max-width: 400px;
    margin: 30px auto;
    background: rgb(207, 106, 106);
    text-align: left;
    padding: 40px;
    border-radius: 10px;
  }
  label {
    color: rgb(12, 15, 17);
    display: inline-block;
    margin: 25px 0 15px;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
  }
  input, select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #990c0c;
    color: #16151555;
  }
  input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    top: 20px;
  }
  button {
    background: rgb(68, 175, 207);
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
  }
  .submit {
    text-align: center;
  }
  .error {
    color: red;
    margin-top: 10px;
    font-size: 1.2em;
    font-weight: bold;
  }
  .pill {
    display: inline-block;
    padding: 5px 10px;
    margin: 5px;
    background-color: #e0e0e0;
    border-radius: 15px;
    cursor: pointer;
  }
  </style>
  