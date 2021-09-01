<template>
  <div>
    <h1>Edtake - Test technique</h1>
    <div class="content">
      <div class="gantt">
        <Gantt
          :tasks="tasks"
          @progressChanged="onProgressChange"
          @dateChanged="onDateChanged"
        />
      </div>
      <div class="table">
        <GanttTable :tasks="tasks" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        {
          id: 'Task 1',
          name: 'Foo task 1',
          start: '2021-01-01',
          end: '2021-01-15',
          progress: 20,
          dependencies: 'Task 2, Task 3',
        },
        {
          id: 'Task 2',
          name: 'Foo task 2',
          start: '2021-01-05',
          end: '2021-01-07',
          progress: 25,
        },
        {
          id: 'Task 3',
          name: 'Foo task 3',
          start: '2021-01-08',
          end: '2021-01-13',
          progress: 50,
        },
        {
          id: 'Task 4',
          name: 'Foo task 4',
          start: '2021-01-01',
          end: '2021-01-11',
          progress: 42,
        },
      ],
    }
  },
  methods: {
    onDateChanged(updatedTask) {
      this.$set(this.tasks, updatedTask._index, updatedTask)
    },
    onProgressChange(updatedTask) {
      this.$set(this.tasks, updatedTask._index, updatedTask)
    },
  },
}
</script>

<style>
.content {
  display: grid;
  grid-gap: 20px;
  grid-template-columns: repeat(10, minmax(100px, 1fr));
  align-items: center;
}
.gantt {
  grid-column: 1 / span 7;
}
.table {
  grid-column: 8 / span 3;
  width: 100%;
}
</style>
