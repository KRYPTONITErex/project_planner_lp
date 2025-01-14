<template>
    <div class="home">
        <h1>Home</h1>

        <div class="projects" v-for="project in projects" :key="project.id">
            <SingleProject :project="project" @delete="deleteProj"></SingleProject>
        </div>
    </div>
  
</template>

<script>
import SingleProject from '../components/SingleProject.vue'
export default {
    data() {
        return {
            projects: []
        }
    },
    name: 'Home',
    components: {
    SingleProject,
        
    },
    mounted() {
        fetch('http://localhost:3000/projects/')
        .then((res)=>{
            return res.json()
        })
        .then((data)=>{
            // console.log(data)
            this.projects = data
        })
    },
    methods:{
        deleteProj(id){
            this.projects = this.projects.filter((project)=>{
                return project.id !== id
            })
        }
    }

}
</script>

<style>

</style>