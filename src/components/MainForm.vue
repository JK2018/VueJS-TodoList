<template>
    <div>
        <h1>New Task</h1>
        <form>
            <div class="form-group">
                <label for="task">Task</label>
                <input v-model="task" type="text" class="form-control" id="task">
                <button v-on:click="submitTask" class="btn btn-primary"> Add task</button>
                <p>{{task}}</p>
            </div>
        </form>


        <h1>Current Tasks</h1>
        <ul>
            <li v-bind:key="index" v-for="(task, index) in tasks">
                <item v-bind:task="task"></item>
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
            this.tasks.append(this.task)
        }
    },
    components: {
        'item': Item
    }
    
}
</script>



<style>

</style>