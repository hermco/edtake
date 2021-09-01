<template>
  <svg id="gantt"></svg>
</template>

<script>
import Gantt from 'frappe-gantt'

export default {
  name: 'Gantt',
  props: { tasks: { type: Array, required: true } },
  data() {
    return { gantt: null }
  },
  watch: {
    tasks() {
      this.gantt.refresh(this.tasks)
    },
  },
  mounted() {
    this.gantt = new Gantt('#gantt', this.tasks, {
      on_date_change: (task, newStart, newEnd) => {
        this.$emit('dateChanged', {
          ...task,
          start: newStart,
          end: newEnd,
        })
      },
      on_progress_change: (task, newProgress) => {
        this.$emit('progressChanged', { ...task, progress: newProgress })
      },
    })
  },
  methods: {},
}
</script>
