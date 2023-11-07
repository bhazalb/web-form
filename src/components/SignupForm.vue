
<template>
   <form @submit.prevent="handleSubmit" >
    <label>Email:</label>
    <input type="email" required  v-model="email">

    <label>Password:</label>
    <input type="password" required  v-model="password">
    <div v-if="passwordError" class="error" > {{ passwordError }} </div>

    <label >Role: </label>
    <select v-model="role">
        <option value="developer"> Web Developer</option>
        <option value="desinger"> Web Desinger </option>
    </select>

    <label>Skills: </label>
    <input type="text" v-model="tempSkill" @keyup="addSkill" >
    <div v-for="skill in skills"  :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{ skill }}</span>
    </div>

   <div class="terms">
    <input type="checkbox" required v-model="terms">
    <label>Acceot terms and conditions</label>
   </div>
   <div class="submit">
    <button>Create an Account</button>
   </div>
   

   </form>


  <p>Email: {{ email}}</p>
  <p>Password: {{ password }} </p>
  <p>Role : {{ role }} </p>
  <p> Terms Accepted:  {{ terms }} </p>
 

</template>
<script>
  export default{
    data() {
        return {
            email: '',
            password: '',
            role : '',
            terms: false , 
            tempSkill: '',
            skills: [],
            passwordError: '',
        }
    },
   methods: {
    addSkill(e){
        if(e.key === ',' && this.tempSkill){
            if(!this.skills.includes(this.tempSkill)) {
                this.skills.push(this.tempSkill)
            }
            
            this.tempSkill =''
        }
    },
    deleteSkill(skill){
    this.skills = this.skills.filter((item) => {
        return skill !== item 
    })
    },
    handleSubmit() {
      //validate password
      this.passwordError =this.password.length > 5 ?
       '' : 'password must be at least 6 chars long '
 
       if(!this.passwordError){
        console.log('email:' , this.email)
        console.log('password:' , this.password)
        console.log('role:' , this.role)
        console.log('terms accepted:' , this.terms)

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
.pill{
    display: inline-block;
    margin: 28px 10px 0 0 ;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}
button{
    background: rgb(0, 42, 105);
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
}
button:hover{
    background: rgb(88, 126, 184);
}
.submit{
    text-align: center;
}
.error{
    color: #ec1010;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
}

</style>