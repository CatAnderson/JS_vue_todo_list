<template>
    <div id="app">
        <h1>To Do List...</h1>
        
        <form v-on:submit.prevent="saveNewTask">
            <label for="new-todo">add new task:</label>
            <input id="new-todo" type="text" v-model="newTask.name">
            <input type="radio" id="high" name="priority" value="high" v-model="newTask.priority" required>
                <label for="high">high</label>
                <input type="radio" id="low" name="priority" value="low" v-model="newTask.priority" required>
                <label for="low">low</label>
            </input>
            <input type="submit" value="save new task">
        </form>
        
        <ul>
            <li v-for="(task, index) in tasks" v-bind:key="index" v-bind:class="task.priority">
                <span> {{ task.name }} </span>
                <!-- <span v-if="task.priority"></span>
                <span v-if="!task.priority" v-on:click="taskPriority(index)"></span> -->
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    data(){
        return {
            tasks: [
                { name: "Buy shopping", priority: 'high' },
                { name: "Clean bathroom", priority: 'high' },
                { name: "Car's MOT", priority: 'low' }
                ],
            newTask: {}
        }
    },

    methods: {
        saveNewTask: function(){
            this.tasks.push(this.newTask);
            this.newTask = {}
        }
    }
}
</script>

<style>
#app {
    width: 60%;
    margin: 0 auto;
    font-family: 'Lato', sans-serif;
}

ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
}

li {
    margin: 20px 0;
    padding: 10px;
    display: flex;
    justify-content: space-between;
}

li span {
    padding: 8px;
}

li button {
    background: #f2360c;
    color: #fff;
    border: none;
    padding: 10px;
    cursor: pointer;
}

li.low {
    border: 2px solid #1a681e;
    color: #1a681e;
}

li.high {
    color: #f2360c;
  border: 2px solid #f2360c;
}

input[type="text"] {
  padding: 10px;
  width: 50%;
  margin:5px;
}

button, input[type="submit"]{
  padding: 10px;
  background: #000;
  color: #fff;
  cursor: pointer;
  border: 1px solid #000;
  margin: 30px;
}
</style>