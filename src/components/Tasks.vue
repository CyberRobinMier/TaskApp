<!--take array of tasks as prop, loop thru them, have a single task component for each one.
This component is only to regulate this looping, so we want a seperate component for the
layout of the singular task. Aka this component is for the layout of ALL the tasks.

-->

<template>
<div :key="task.id" v-for="task in tasks">
    <Task @delete-task="$emit('delete-task', task.id)" :task="task"/>

</div>
    
</template>

<script>
import Task from './Task.vue'
export default{
    name: 'Tasks',
    props:{
        tasks: Array
    },
    components: {
        Task
    },
    emits:['delete-task'], // an array of events that we are emitting upwards

}

</script>