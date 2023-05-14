<template>
    <form @submit="onSubmit" class="add-form">
      <div class="form-control">
        <label>Schedule</label>
        <input type="text" v-model="text" name="text" placeholder="Add Schedule" />
      </div>
      <div class="form-control">
        <label>Day & Time</label>
        <input
          type="text"
          v-model="day"
          name="day"
          placeholder="Add Day & Time"
        />
      </div>
      <div class="form-control form-control-check">
        <label>Set Reminder</label>
        <input type="checkbox" v-model="reminder" name="reminder" />
      </div>
  
      <input type="submit" value="Save Schedule" class="btn btn-block" />
    </form>
  </template>

<script>
    export default {
        name: "AddSchedule",
        data() {
            return {
                text: '',
                day: '',
                reminder: false

            }
        },
        methods: {
            // https://qiita.com/yokoto/items/27c56ebc4b818167ef9e
            onSubmit(e) {
                e.preventDefault()

                if (!this.text) {
                    alert('Please add a schedule')
                    return
                }

                const newSchedule = {
                    id: Math.floor(Math.random() * 100000),
                    text: this.text,
                    day: this.day,
                    reminder: this.reminder,
                }

                this.$emit('add-schedule', newSchedule)

                this.text = ''
                this.day = ''
                this.reminder = false
            },
        },

    }
</script>


<style scoped>
.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px 0;
}

.form-control label {
  display: block;
}

.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.form-control-check label {
  flex: 1;
}

.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>