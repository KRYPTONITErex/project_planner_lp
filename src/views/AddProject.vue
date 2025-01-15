<template>

<div class="title"><h1>Add Project</h1></div>


  <div>
      <form @submit.prevent="addProject">
            <label for="">Project Title</label>
            <input v-model="title" type="text" placeholder="Title">
            <label  for="">Project Details</label>
            <input v-model="description" type="text" placeholder="Project Details">
            <button type="submit">Add Project</button>
      </form>
  </div>
</template>


<script>
export default {
    data() {
        return {
            title: '',
            description: ''
        }
    },
    methods: {
        addProject(){
            // console.log('add project')
            fetch('http://localhost:3000/projects', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    title: this.title,
                    description: this.description,
                    completed: false
                })
            })
            .then(()=>{
                //redirect to home page
                this.$router.push({name: 'home'})
            })
       
        }
    }
}
</script>



  
  <style scoped>
  /* Full background styling */
  body {
    margin: 0;
    padding: 0;
    height: 100vh;
    background: linear-gradient(135deg, #1e3c72, #2a5298); /* Rich gradient background */
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
  }
  
  /* Title styling */
  .title {
    text-align: center;
    margin-top: 50px;
    color: #ffffff;
    font-size: 28px;
    font-weight: bold;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
    margin-bottom: 20px;    
  }
  
  /* Center the form container */
  .form-container {
    position: absolute;
    top: 30%; /* Position the form 30% from the top */
    left: 50%; /* Center horizontally */
    transform: translate(-50%, -30%);
    width: 100%;
    max-width: 400px; /* Prevent the form from being too wide */
    text-align: center;
    color: #ffffff;
    font-size: 14px;
    font-weight: bold;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
    margin-bottom: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;

  }
  
  /* Form styling */
  form {
    background-color: #ffffff;
    padding: 30px 40px;
    border-radius: 15px;
    box-shadow: 0 6px 20px rgba(0, 0, 0, 0.2);
  }
  
  /* Label styling */
  form label {
    display: block;
    margin-bottom: 10px;
    font-weight: bold;
    color: #444;
    font-size: 14px;
    
  }
  
  /* Input fields styling */
  form input[type="text"] {
    width: 90%;
    padding: 12px;
    margin-bottom: 20px;
    border: 1px solid #ccc;
    border-radius: 10px;
    font-size: 14px;
    box-shadow: inset 0 2px 5px rgba(0, 0, 0, 0.1);
    align-items: center;
    align-content: center;

  }
  
  form input[type="text"]:focus {
    border-color: #1e88e5;
    outline: none;
    box-shadow: 0 0 5px rgba(30, 136, 229, 0.5);
    transition: box-shadow 0.3s ease-in-out;
    align-items: center;
    align-content: center;

  }
  
  /* Submit button styling */
  form button[type="submit"] {
    width: 70%;
    padding: 15px;
    font-size: 16px;
    color: #ffffff;
    background-color: #1e88e5;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: background-color 0.3s;
    align-items: center;
    align-content: center;
    margin-left: 15%;
    margin-right: 15%;
    margin-top: 20px;
    margin-bottom: 20px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);

  }
  
  form button[type="submit"]:hover {
    background-color: #1565c0;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);

  }
  </style>