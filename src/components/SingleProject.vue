<template>
    <div class="div1" v-for="task in tasks" :key="task.id" >
        <div class="task-card" :class="{done: task.completed}">
            <div class="div2" @click="show(task.id)"><h2>{{task.task}}</h2></div>

            <div class="icons">

                <router-link :to="{name: 'EditProject', params: {id: task.id}}">
                    <span class="material-symbols-outlined">edit_square</span>
                </router-link>

                <span @click="completed(task.id)" class="material-symbols-outlined">task_alt</span>
                <span @click="deletePj(task.id)" class="material-symbols-outlined">scan_delete</span>
            </div>
        </div>
           
        <div v-if="selectedTaskId === task.id">
                <p>{{task.completed}}</p>
                <p>{{task.priority}}</p>
                <h3>{{task.description}}</h3>
                <p>{{task.category}}</p>
                
        </div>
    </div>

</template>

<script>
export default {
    data() {
        return {
            tasks: [],
            selectedTaskId: null,

        }
    },

    mounted() {
        fetch('http://localhost:3003/tasks/')
        .then((res)=>{
            return res.json()
        })
        .then((data)=>{
            this.tasks = data
        })
    },
    methods: {
        show(id) {
            this.selectedTaskId = this.selectedTaskId === id ? null : id
        },
        deletePj(id) {
            // console.log('task.id', id)
            let deleteRoute = 'http://localhost:3003/tasks/' + id
            fetch(deleteRoute,{method: 'DELETE'})
            .then((res)=>{
                this.tasks = this.tasks.filter((task) => {
                    return task.id !== id
                })
            })
            .catch((err)=>{
                console.log(err)
            })
        },
        completed(id) {
            
            let task = this.tasks.find((task) =>{
                return task.id === id
            })
    
            // console.log('completed')
            let completedRoute = 'http://localhost:3003/tasks/' + id
           fetch(completedRoute, {method: 'PATCH',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    completed: !task.completed
                })
            })
            .then((res)=>{
                return res.json()
            })
            .then(()=>{
                task.completed = !task.completed
            })
          
        }
    }
    

}
</script>

<style>
/* Root container for all tasks */
.div1 {
    display: block;
    margin: 0 auto;
    max-width: 1200px; /* Adjust as needed */
    gap: 16px; /* Space between task cards */
    padding: 16px;
    background-color: #f4f4f4; /* Light background for the overall container */
    justify-content: flex-start; /* Align items to the left */
}

/* Task card styling */
.div1 {
    margin: 20px;
    flex-direction: column; /* Arrange details vertically within each card */
    background-color: #fff; /* White background for individual task cards */
    border: 1px solid #ddd; /* Subtle border */
    border-radius: 8px; /* Rounded corners */
    padding: 16px; /* Padding inside the card */
    width: 300px; /* Fixed width for uniformity */
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Subtle shadow for depth */
    transition: transform 0.2s, box-shadow 0.2s; /* Smooth hover effect */
}

/* Hover effect for task cards */
.div1:hover {
    transform: translateY(-4px); /* Lift the card slightly */
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.15); /* Enhance shadow on hover */
}
.task-card:hover {
    transform: translateY(-4px); /* Lift the card slightly */
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.15); /* Enhance shadow on hover */
}

/* Task title styling */
h2 {
    font-size: 1.25rem; /* Slightly larger font size */
    font-weight: bold; /* Bold font for task title */
    color: #333; /* Darker text color for better contrast */
    margin-bottom: 8px; /* Space below the title */
    text-align: center; /* Center the task title */
}

/* Task detail styling */
h3 {
    font-size: 1rem;
    color: #555; /* Softer color for task descriptions */
    margin-bottom: 8px;
}

/* General text styling for additional details */
p {
    font-size: 0.9rem; /* Standard text size */
    color: #666; /* Neutral color for routine task details */
    margin: 4px 0; /* Space between details */
    line-height: 1.4; /* Improve readability */
}

/* Special styling for completed status */
p:nth-of-type(1) {
    font-weight: bold;
    color: green; /* Highlight completed status */
}

.task-card{
    /* border-bottom: crimson 5px solid; */
    border-right: crimson 5px solid;
    border-radius: 10px 0px 10px 10px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    transition: 0.3s;
}

.material-symbols-outlined {
    margin: 6px;
    cursor: pointer;
}

.done {
    border-right: rgb(32, 214, 32) 5px solid;
}
  
</style>