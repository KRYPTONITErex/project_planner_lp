<template>

    <div class="project">
        <div class="project-title" >
            <div>
                <h2 @click="show">{{ project.title }}</h2>
            </div>
            <div class="icons">
                <span class="material-symbols-outlined">edit_square</span>
                <span class="material-symbols-outlined">task_alt</span>
                <span @click="deleteProj" class="material-symbols-outlined">scan_delete</span>
            </div>
        </div>
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
        }
    }

}
</script>

<style>
.project {
    background-color: #f9f9f9; /* Light gray background */
    border: 1px solid #ddd; /* Subtle border */
    border-radius: 8px; /* Rounded corners */
    padding: 16px; /* Spacing inside the card */
    margin-bottom: 16px; /* Space between project cards */
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Subtle shadow for depth */
    transition: transform 0.2s, box-shadow 0.2s; /* Smooth hover effect */
    border-right: crimson 4px solid;
}

.project:hover {
    transform: translateY(-4px); /* Slight lift on hover */
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.15); /* Enhanced shadow on hover */
}

.project-title {
    font-size: 1.5rem; /* Slightly larger font for title */
    font-weight: bold; /* Make the title stand out */
    color: #333; /* Darker text for contrast */
    margin-bottom: 8px; /* Space below the title */
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
    line-height: 1.6; /* Improve readability */
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
</style>