
<template>
<h1>Task List</h1>

<table class="table table-bordered">
<thead>
<tr>
<th> ID </th>
<th> Title </th>
<th> Completed </th>
</tr>
</thead>
<tbody>
<tr>
<td>1</td>
<td>3</td>
<td>2</td>

</tr>
<tr v-for="(task , index) in this.tasks" :key="index">
<td>{{task.id}}</td>
<td>{{task.title}}</td>
<td>{{task.completed}}</td>
</tr>
</tbody>
</table>
</template>

<script>
import 'bootstrap';
import axios from 'axios';

export default{
    name: 'tasks',
    data(){
        return{
            tasks:[]
        }
    },

    mounted(){
        this.getTasks();
        console.log('Test i am here!!');
    },
    methods:{
        getTasks(){
            axios.get('https://jsonplaceholder.typicode.com/todos').then(res=>{
                    this.tasks = res.data         
                    console.log(this.tasks)
                    //console.log(res);
            });
        }
    },
}
</script>


<style scoped>

table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  border: 1px solid black;
}



</style>