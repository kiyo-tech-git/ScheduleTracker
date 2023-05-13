<template>
    <div>
        <span :key="ki_schedule.id" v-for="ki_schedule in ki_schedules">
            <KI_Schedule @toggle-reminder="$emit('toggle-reminder', ki_schedule.id)" @delete-schedule="$emit('delete-schedule', ki_schedule.id)"  :ki_schedule="ki_schedule" />
        </span>
    </div>

</template>


<script>
    import KI_Schedule from './Schedule'
    export default{
        name: "KI_Schedules",
        props: {
            ki_schedules: Array
        },
        components:{
            KI_Schedule
        },
    }
</script>