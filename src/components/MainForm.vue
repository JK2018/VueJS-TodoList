<template>
    <div id="mainDiv">
        <h1>New Task</h1>
        <form>
            <div class="form-group">
                <label for="task">Task</label>
                <input v-model="formData.task" type="text" class="form-control" id="task">
                <button v-on:click.prevent="submitTask" class="btn btn-primary"> Add task</button>
                
            </div>
        </form>

        
        <h1>Current Tasks</h1>
        <ul>
            <li v-bind:key="index" v-for="(task, index) in tasks">
                <item v-bind:id="index" :deleteTask="deleteTask" v-bind:task="task"></item>
            </li>
        </ul>
    </div>
</template>




<script>
import Item from './Item'
export default {
    name: 'MainForm',
    data() {
        return{
            formData: {
                task: ''
            },
            tasks: ['python', 'react', 'java', 'php']
            
        }
    },
    methods: {
        submitTask: function(){
            this.tasks.push(this.formData.task);
            this.formData.task = ' '
        },
        deleteTask: function(e){
            this.tasks.splice(e.target.parentNode.id, 1)
        }
    },
    components: {
        'item': Item
    }
    
}
</script>



<style>
    li{
        list-style-type: none;
        padding: 0;
    }
    #mainDiv{
        width:50%; 
        margin:auto;
    }
</style>