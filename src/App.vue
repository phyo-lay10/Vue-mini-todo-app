<template>
  <div class="container my-5">
    <div class="row">
      <div class="col-md-6">
        <h3 class="text-decoration-underline mb-3">Vue-Todo-App</h3>

        <div class="p-4 rounded mb-5 shadow-lg">
          <input
            type="text"
            @keyup.enter="addList"
            v-model="inputTodo"
            placeholder="Add to do list"
            class="form-control shadow"
            :class="{ 'is-invalid': inputInvalid }"
          />
          <div v-if="inputInvalid" class="invalid-feedback">
            You need to fill this field.
          </div>
          <button class="btn btn-sm btn-primary mt-4" @click="addList">
            {{ editingTodo ? "Update" : "Add" }}
          </button>
        </div>

        <h5 class="mb-3">Todo Lists ~</h5>
        <ul class="list-group">
          <li
            class="list-group-item shadow-sm d-flex justify-content-between pt-3 mb-3"
            v-for="todo in todos"
            :key="todo.id"
            @dblclick="doneTodo(todo)"
          >
            <p>
              <b>~ </b>
              <span style="cursor: pointer" title="double click">
                <i> {{ todo.name }}</i></span
              >
            </p>
            <div>
              <button
                title="edit"
                class="btn btn-sm btn-outline-info"
                @click="editTodo(todo)"
              >
                <i class="bi bi-pencil-square"></i>
              </button>
              <button
                title="done"
                class="btn btn-sm btn-outline-primary mx-2"
                @click="doneTodo(todo)"
              >
                <i class="bi bi-check-square"></i>
              </button>
              <button
                title="delete"
                class="btn btn-sm btn-outline-danger"
                @click="deleteTodo(todo.id)"
              >
                <i class="bi bi-trash"></i>
              </button>
            </div>
          </li>
        </ul>
      </div>
      <div class="col-md-6 ps-5 mt-2">
        <h5 class="mb-4">Done todo lists ~</h5>
        <ul class="list-group">
          <li
            class="list-group-item shadow-sm d-flex justify-content-between pt-3 mb-3"
            v-for="doneTodo in doneTodos"
            :key="doneTodo.id"
            @dblclick="undoneTodo(doneTodo)"
          >
            <p>
              <b>~ </b>
              <span style="cursor: pointer" title="double click">
                <i> {{ doneTodo.name }}</i></span
              >
            </p>
            <div>
              <button
                title="undone"
                class="btn btn-sm btn-outline-primary mx-2"
                @click="undoneTodo(doneTodo)"
              >
                <i class="bi bi-arrow-counterclockwise"></i>
              </button>
              <button
                title="delete"
                class="btn btn-sm btn-outline-danger"
                @click="deleteDoneTodo(doneTodo)"
              >
                <i class="bi bi-trash"></i>
              </button>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const Id = Math.floor(Math.random() * 10) + 1;
const inputTodo = ref("");
const editingTodo = ref();
const doneTodos = ref([]);
const inputInvalid = ref(false);
const todos = ref([
  {
    id: Id,
    name: "wake up early",
    // done: false,
  },
]);

// create
const addList = () => {
  if (inputTodo.value.trim() !== "") {
    // update
    if (editingTodo.value) {
      editingTodo.value.name = inputTodo.value;
      editingTodo.value = "";
      inputTodo.value = "";
    } else {
      const newTodo = {
        id: Math.floor(Math.random() * 10),
        name: inputTodo.value,
        done: false,
      };
      todos.value.push(newTodo);
      inputTodo.value = "";
    }
  } else {
    inputInvalid.value = true;
  }
};

// edit
const editTodo = (todo) => {
  editingTodo.value = todo;
  inputTodo.value = todo.name;
};

// delete
const deleteTodo = (id) => {
  todos.value = todos.value.filter((todo) => todo.id !== id);
};

// done
const doneTodo = (todo) => {
  todo.done = true;
  doneTodos.value.push(todo);
  todos.value = todos.value.filter((t) => t !== todo);
};

// undone
const undoneTodo = (doneTodo) => {
  doneTodo.done = false;
  todos.value.push(doneTodo);
  doneTodos.value = doneTodos.value.filter((t) => t !== doneTodo);
};

// delete doneTodo
const deleteDoneTodo = (doneTodo) => {
  doneTodos.value = doneTodos.value.filter((t) => t !== doneTodo);
};
</script>

<style scoped></style>
