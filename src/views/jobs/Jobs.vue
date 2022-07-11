<template>
    <h1>Jobs</h1>
    <rout v-for="job in jobs" :key="job.id" class="p"> 
        <router-link :to="{name:'jobDetail', params:{id:job.id}}">
            <p>{{ job.title }}</p>
        </router-link>
    </rout>
</template>
	
<script>
export default {
    data() {
        return {
            jobs: []
        };
    },
    mounted() {
        fetch("http://localhost:3000/jobs")
        .then(((response)=>{
            return response.json();
        }))
        .then((datas)=>{
            this.jobs = datas;
            console.log(this.jobs)
        })
        .catch((err)=>{
            console.log(err.message);
        })
    }
};
</script>
<style>
h3 {
    color: crimson;
}
.p p {
    color: black;
    text-decoration: none;
    text-transform: uppercase;
    letter-spacing: 2px;
}
</style>