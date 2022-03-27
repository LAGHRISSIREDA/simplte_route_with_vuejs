<template>
  <div v-if="job">
      <h1>Job Details Page</h1>
      <h3>{{id}}</h3>
      <p>{{job.title}}</p>
  </div>
  <div v-else>
    <p>Loading Job Details ...</p>
  </div>
  
</template>

<script>
export default {
    props:['id'],
    data(){
      return{
        job:null
      }
    },
    mounted(){
      fetch('http://localhost:3000/jobs/'+this.id)
      .then(res=>res.json())
      .then(data=>this.job=data)
      .catch(err=>console.log(err.message))
    }
// data(){
//     return{
//         id: this.$route.params.id
//     }
// }
}
</script>

<style>

</style>