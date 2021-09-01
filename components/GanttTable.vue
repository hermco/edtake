<template>
  <table>
    <thead>
      <tr>
        <th>id</th>
        <th>name</th>
        <th>start</th>
        <th>end</th>
        <th>progress</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="task in tasks" :key="task.id">
        <td>{{ task.id }}</td>
        <td>{{ task.name }}</td>
        <td>{{ getReadableDate(task.start) }}</td>
        <td>{{ getReadableDate(task.end) }}</td>
        <td>{{ task.progress }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import moment from 'moment'

export default {
  props: { tasks: { type: Array, required: true } },
  methods: {
    getReadableDate(date) {
      return moment(date).format('YYYY-MM-DD')
    },
  },
}
</script>

<style>
table {
  width: 100%;
}
table,
td {
  border: 1px solid #333;
}

thead,
tfoot {
  background-color: #333;
  color: #fff;
}
</style>
