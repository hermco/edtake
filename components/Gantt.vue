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
      on_date_change: (task, start, end) => {
        this.$emit('dateChanged', {
          ...task,
          start,
          end,
        })
      },
      on_progress_change: (task, progress) => {
        this.$emit('progressChanged', { ...task, progress })
      },
    })
  },
  methods: {},
}
</script>
