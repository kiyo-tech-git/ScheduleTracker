<template>
  <div class="container">
    <KI_HEADER title='Schedule Tracker' @toggle-add-schedule="toggleAddSchedule" />
    <AddSchedule v-show="showAddSchedule" @add-schedule="addSchedule" />
    <KI_Schedules @delete-schedule="deleteSchedule" @toggle-reminder="toggleReminder" :ki_schedules="ki_schedules" />
  </div>
</template>

<script>
import KI_HEADER from './components/Header'
import KI_Schedules from './components/Schedules'
import AddSchedule from './components/AddSchedule'

export default {
  name: 'App',
  components: {
    KI_HEADER,
    KI_Schedules,
    AddSchedule,
  },
  data() {
    return {
      ki_schedules: [],
      showAddSchedule: false
    }
  },
  methods:{
    toggleAddSchedule(){
      this.showAddSchedule = !this.showAddSchedule
    },
    addSchedule(schedule){
      this.ki_schedules = [...this.ki_schedules, schedule]
      
    },
    deleteSchedule(id) {
      if (confirm('Are your sure?')){
        this.ki_schedules = this.ki_schedules.filter((ki_schedule) => ki_schedule.id !== id)
      }
    },
    toggleReminder(id) {
      console.log("kk");
      this.ki_schedules = this.ki_schedules.map((ki_schedule) => ki_schedule.id === id ? {...ki_schedule, reminder: !ki_schedule.reminder} : ki_schedule)
    }
  },
  created(){
    this.ki_schedules = [
      {
        id: 1,
        text: 'Docter appointment',
        day: '2023/5/16',
        reminder: true,
      },
      {
        id: 2,
        text: 'Docter appointment',
        day: '2023/5/17',
        reminder: true,
      },
      {
        id: 3,
        text: 'Docter appointment',
        day: '2023/5/19',
        reminder: false,
      }
    ]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
