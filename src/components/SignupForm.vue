
<template>
   <form >
    <label>Email:</label>
    <input type="email" required  v-model="email">

    <label>Password:</label>
    <input type="password" required  v-model="password">

    <label >Role: </label>
    <select v-model="role">
        <option value="developer"> Web Developer</option>
        <option value="desinger"> Web Desinger </option>
    </select>

    <label>Skills: </label>
    <input type="text" v-model="tempSkill" @keyup="addSkill" >
    <div v-for="skill in skills"  :key="skill">,
      
    </div>

   <div class="terms">
    <input type="checkbox" required v-model="terms">
    <label>Acceot terms and conditions</label>
   </div>

   

   </form>


  <p>Email: {{ email}}</p>
  <p>Password: {{ password }} </p>
  <p>Role : {{ role }} </p>
  <p> Terms Accepted:  {{ terms }} </p>
  <p>Skill: {{ tempSkill }} </p>

</template>
<script>
  export default{
    data() {
        return {
            email: '',
            password: '',
            role : '',
            terms: false , 
            skills: [],
        }
    },
   methods: {
    addSkill(e){
        if(e.key === ',' && this.tempSkill){
            this.skills.push(this.tempSkill)
            this.tempSkill =''
        }
    }
   }
     
  }



</script>
<style>
form{
    max-width: 420px;
    margin: 30px auto;
    background-color: #ffffff;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}
label{
    color: rgb(0, 0, 0);
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.5rem;
    text-transform: uppercase;
    font-weight: bold;
}
input, select{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: rgb(99, 99, 99);
}
input[type="checkbox"]{
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}

</style>