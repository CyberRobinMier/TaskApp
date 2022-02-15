<!--take array of tasks as prop, loop thru them, have a single task component for each one-->

<template>
<div :key="task.id" v-for="task in tasks">
    <h3>{{task.text}}</h3>

</div>
    
</template>

<script>
export default{
    name: 'Tasks',
    props:{
        tasks: Array
    }

}

</script>