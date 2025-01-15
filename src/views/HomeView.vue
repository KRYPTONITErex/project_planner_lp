<template>
    <div class="home">
        <h1>Home</h1>
        {{ current }}


        <FilterNav :current="current" @filtervalue="current = $event"></FilterNav>

        <div class="projects" v-for="project in filteredProjects" :key="project.id">
            <SingleProject @complete="complete" :project="project" @delete="deleteProj"></SingleProject>
        </div>
    </div>

  
</template>

<script>
import FilterNav from '../components/FilterNav'
import SingleProject from '../components/SingleProject.vue'
export default {
    data() {
        return {
            current: 'All',
            projects: []
        }
    },
    name: 'Home',
    components: {
    FilterNav,
    SingleProject,
        
    },
    computed: {
        filteredProjects() {
            if(this.current === 'Completed') {
                return this.projects.filter((project)=>{
                    return project.completed
                })
            }

            if(this.current === 'Ongoing') {
                return this.projects.filter((project)=>{
                    return !project.completed
                })
            }

            return this.projects
        }
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
        },
        complete(id){
            let project = this.projects.find((project)=>{
                return project.id === id
            })
            project.completed = !project.completed
        }
    }
   

}
</script>

<style>

</style>