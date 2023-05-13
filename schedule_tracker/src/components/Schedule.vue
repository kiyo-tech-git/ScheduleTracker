<template>
    <div @dblclick="$emit('toggle-reminder')" v-bind:class="[ki_schedule.reminder ? 'reminder' : '', 'schedule']">
        <h3>
            {{ ki_schedule.text }}
            <i @click="onDelete()" class="fas fa-times"></i>
        </h3>
        <p>{{ ki_schedule.day }}</p>
    </div>
</template>

<script>
export default{
    name: "KI_Schedule",
    props:{
        ki_schedule: Object,
    },
    methods:{
        onDelete(){
            this.$emit('delete-schedule')

        }
    }
}
</script>

<style scoped>
.schedule {
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}


.schedule h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.fas {
    color: red;
}


.schedule.reminder {
  border-left: 5px solid green;
}
</style>