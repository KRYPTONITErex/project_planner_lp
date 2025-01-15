<template>
    <div>

        <h1>Edit Project</h1>

        <p>{{ id }}</p>


  <div>
      <form @submit.prevent="addProject">
            <label for="">Project Title</label>
            <input v-model="title" type="text" placeholder="Title">
            <label  for="">Project Details</label>
            <input v-model="description" type="text" placeholder="Project Details">
            <button @click="updateProj" type="submit">Update Project</button>
      </form>
  </div>

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
    props: ['id'],
    mounted() {
        fetch('http://localhost:3000/projects/' + this.id)

        .then((res)=>{
            return res.json()
        })
        .then((data)=>{
            this.title = data.title
            this.description = data.description
        })
    },
    methods: {
        updateProj(){
            // console.log('update project')
            fetch('http://localhost:3000/projects/' + this.id, {
                method: 'PATCH',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    title: this.title,
                    description: this.description
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
  background: linear-gradient(120deg, #0f2027, #203a43, #2c5364); /* Sleek gradient background */
  font-family: 'Poppins', sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Center the form container */
.form-container {
  position: relative;
  width: 90%;
  max-width: 500px;
  background: rgba(255, 255, 255, 0.95); /* Light background with slight transparency */
  padding: 40px 30px;
  border-radius: 20px;
  box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.2);
  text-align: center;
}

/* Title styling */
h1 {
  font-size: 2rem;
  margin-bottom: 10px;
  color: #2c5364;
  font-weight: bold;
}

/* Subtitle styling */
p {
  font-size: 0.9rem;
  color: #555;
  margin-bottom: 30px;
}

/* Label styling */
form label {
  display: block;
  margin-bottom: 8px;
  font-size: 1rem;
  font-weight: 600;
  color: #333;
  text-align: left;
}

/* Input fields styling */
form input[type="text"] {
  width: 90%;
  padding: 12px 15px;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 10px;
  font-size: 1rem;
  color: #444;
  box-shadow: inset 0 2px 5px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

form input[type="text"]:focus {
  border-color: #2c5364;
  box-shadow: 0 0 8px rgba(44, 83, 100, 0.4);
  outline: none;
}

/* Submit button styling */
form button[type="submit"] {
  width: 100%;
  padding: 12px;
  font-size: 1.2rem;
  font-weight: bold;
  color: #fff;
  background: linear-gradient(135deg, #2c5364, #203a43);
  border: none;
  border-radius: 5px 25px 5px 20px;
  cursor: pointer;
  transition: background 0.3s ease;
}

form button[type="submit"]:hover {
  background: linear-gradient(135deg, #203a43, #0f2027);
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .form-container {
    padding: 30px 20px;
  }

  h1 {
    font-size: 1.8rem;
  }

  form input[type="text"] {
    font-size: 0.9rem;
  }

  form button[type="submit"] {
    font-size: 1rem;
  }
}
</style>