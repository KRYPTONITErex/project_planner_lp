<template>

    <div class="project" :class="{completed: project.completed}">
        <div class="project-title" >
            <div>
                <h4 @click="show">{{ project.title }}</h4>
            </div>
            <div class="icons">
                <span class="material-symbols-outlined">edit_square</span>
                <span @click="completeProj" class="material-symbols-outlined">task_alt</span>
                <span @click="deleteProj" class="material-symbols-outlined">scan_delete</span>
            </div>
        </div>
        <p>{{ project.completed }}</p>

        <div v-if="showDescription">
            <p>{{ project.description }}</p><hr>
        </div>
    </div>
   
</template>

<script>
export default {
    data() {
        return {
            showDescription: false,
            api: 'http://localhost:3000/projects/'
        }
    },
    props: ['project'],
    methods: {
        show() {
            this.showDescription = !this.showDescription
        },
        deleteProj() {
            let deleteRoute = this.api + this.project.id
            console.log('deleteRoute')
            fetch(deleteRoute,{method: 'DELETE'})
            .then(()=>{
                this.$emit('delete', this.project.id)
            })
            .catch((err)=>{
                console.log(err)
            })
        },
        completeProj() {
            let updateCompleteroute = this.api + this.project.id
            fetch(updateCompleteroute, {method:'PATCH',
                headers: {
                    'Content-Type' : 'application/json'
                },
                body: JSON.stringify(
                    {
                    completed: !this.project.completed
                })
            })
            .then(()=>{
                this.$emit('complete', this.project.id)
            })
            .catch((err)=>{
                console.log(err)
            })
        }
    }

}
</script>

<style>
.project {
    background-color: #f9f9f9; /* Light gray background */
    border: 1px solid #ddd; /* Subtle border */
    border-radius: 30px 5px 20px 0; /* Rounded corners */
    padding-left: 30px; /* Spacing inside the card */
    margin-bottom: 16px; /* Space between project cards */
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Subtle shadow for depth */
    transition: transform 0.2s, box-shadow 0.2s; /* Smooth hover effect */
    border-right: rgb(240, 60, 96) 10px solid;
}

.project:hover {
    transform: translateY(-4px); /* Slight lift on hover */
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.15); /* Enhanced shadow on hover */
}

.project-title {
    font-size: 1.2rem; /* Slightly larger font for title */
    font-weight: bold; /* Make the title stand out */
    color: #333; /* Darker text for contrast */
    margin-bottom: 2px; /* Space below the title */
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.project-title h2 {
    margin: 0; /* Remove default margin */
}

.project p {
    font-size: 1rem; /* Standard text size */
    color: #555; /* Softer text color for the description */
    line-height: 2; /* Improve readability */
    margin: 0; /* Remove default margin */
}

hr {
    border: 0;
    border-top: 1px solid #ddd; /* Subtle horizontal line */
    margin: 16px 0; /* Space above and below the line */
}

.icons {
    display: flex;
    gap: 10px;
    cursor: pointer;
}

.completed {
    border-right: rgba(103, 219, 1, 0.801) 10px solid;
}
</style>