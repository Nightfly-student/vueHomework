<template>
  <div>
    <table>
      <tr>
        <th>ID</th>
        <th>TASK</th>
        <th>COMPLETED</th>
      </tr>
      <tbody>
        <tr v-for="to in todo" :key="to.id">
          <td>{{ to.id }}</td>
          <td>{{ to.task }}</td>
          <td>
            {{ to.status }}
            <input
              :checked="to.status"
              @change="changeStatus(to)"
              type="checkbox"
            />
          </td>
        </tr>
      </tbody>
    </table>
    <input v-model="add" type="text" placeholder="type task" />
    <button @click="addTask(add)">Add</button>
  </div>
</template>

<script>
export default {
  name: "ToDo",
  data() {
    return {
      todo: [
        { id: 1, task: "pizza halen", status: false },
        { id: 2, task: "drank halen", status: true },
        { id: 3, task: "patat halen", status: false },
      ],
    };
  },
  methods: {
    changeStatus(e) {
      e.status = e.status ? false : true;
    },
    addTask(task) {
      if (task == "" || task == null) {
        alert("Please Enter a Task First");
      } else {
        this.todo.push({ id: this.todo.length+1, task: task, status: false });
      }
    },
  },
};
</script>

<style>
table {
  width: 100%;
  border-collapse: collapse;
}
table tr {
  color: black;
}
table tbody tr:nth-of-type(odd) {
  background: rgb(228, 228, 228);
}
table tbody tr:nth-of-type(even) {
  background: rgb(245, 245, 245);
}
table td,
table th {
  text-align: left;
  border: 0.1ren solid #e4e4e4;
  padding: 0.5rem;
}
</style>
