<!-- <template>
  <div class="container p-5">
    <h4>My Todo Lists</h4>
    <div class="input-group w-50">
      <input type="text" v-model="inputTodo" class="form-control" />
      <button class="btn btn-primary" @click="addList">
        {{ editingTodo ? "Update" : "Add" }}
      </button>
    </div>

    <h5 class="mt-3">Todo List</h5>
    <ul>
      <li
        v-for="todo in todos"
        :key="todo.id"
        class="mt-3"
        @dblclick="markAsDone(todo)"
        title="double click"
      >
        <span style="cursor: pointer">{{ todo.name }}</span>
        <button class="btn btn-sm btn-success mx-2" @click="markAsDone(todo)">
          Done
        </button>
        <button class="btn btn-sm btn-warning mx-2" @click="editTodo(todo)">
          Edit
        </button>
        <button class="btn btn-sm btn-danger" @click="deleteTodo(todo)">
          Delete
        </button>
      </li>
    </ul>

    <h5 class="mt-5">Done List</h5>
    <ul>
      <li
        v-for="doneTodo in doneTodos"
        :key="doneTodo.id"
        @dblclick="markAsUndone(doneTodo)"
      >
        <span style="cursor: pointer">{{ doneTodo.name }}</span>
        <button
          class="btn btn-sm btn-warning border mx-2"
          @click="markAsUndone(doneTodo)"
        >
          Undone
        </button>
        <button
          class="btn btn-sm btn-danger border"
          @click="deleteDone(doneTodo)"
        >
          Delete
        </button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from "vue";

const Id = Math.floor(Math.random() * 10) + 1;
const todos = ref([]);
const doneTodos = ref([]);
const inputTodo = ref("");
const editingTodo = ref(null);

const addList = () => {
  if (inputTodo.value !== "") {
    if (editingTodo.value) {
      // Update existing todo
      editingTodo.value.name = inputTodo.value;
      editingTodo.value = null;
    } else {
      // Add new todo
      const newTodo = {
        id: Id,
        name: inputTodo.value,
        done: false,
      };
      todos.value.push(newTodo);
    }
    inputTodo.value = "";
  }
};

const markAsDone = (todo) => {
  todo.done = true;
  doneTodos.value.push(todo);
  todos.value = todos.value.filter((t) => t !== todo);
};

const markAsUndone = (doneTodo) => {
  doneTodo.done = false;
  todos.value.push(doneTodo);
  doneTodos.value = doneTodos.value.filter((t) => t !== doneTodo);
};

const deleteTodo = (todo) => {
  todos.value = todos.value.filter((t) => t !== todo);
};

const deleteDone = (doneTodo) => {
  doneTodos.value = doneTodos.value.filter((t) => t !== doneTodo);
};

const editTodo = (todo) => {
  editingTodo.value = todo;
  inputTodo.value = todo.name;
};
</script>

<style scoped></style> -->

<!-- <template>
  <div class="container p-5">
    <h4>My Todo Lists</h4>
    <div class="input-group w-50">
      <input type="text" v-model="inputTodo" class="form-control" />
      <button class="btn btn-primary" @click="addList">Add</button>
    </div>

    <h5 class="mt-3">Todo List</h5>
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        {{ todo.name }}
        <button class="btn btn-sm btn-success mx-2" @click="markAsDone(todo)">
          Done
        </button>
        <button class="btn btn-sm btn-danger" @click="deleteTodo(todo)">
          Delete
        </button>
      </li>
    </ul>

    <h5 class="mt-5">Done List</h5>
    <ul>
      <li v-for="doneTodo in doneTodos" :key="doneTodo.id">
        {{ doneTodo.name }}
        <button
          class="btn btn-sm btn-warning border mx-2"
          @click="markAsUndone(doneTodo)"
        >
          Undone
        </button>
        <button
          class="btn btn-sm btn-danger border"
          @click="deleteDone(doneTodo)"
        >
          Delete
        </button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from "vue";

const Id = Math.floor(Math.random() * 10) + 1;
const todos = ref([]);
const doneTodos = ref([]);
const inputTodo = ref("");

const addList = () => {
  if (inputTodo.value !== "") {
    const newTodo = {
      id: Id,
      name: inputTodo.value,
      done: false,
    };
    todos.value.push(newTodo);
    inputTodo.value = "";
  }
};

const markAsDone = (todo) => {
  todo.done = true;
  doneTodos.value.push(todo);
  todos.value = todos.value.filter((t) => t !== todo);
};

const markAsUndone = (doneTodo) => {
  doneTodo.done = false;
  todos.value.push(doneTodo);
  doneTodos.value = doneTodos.value.filter((t) => t !== doneTodo);
};

const deleteTodo = (todo) => {
  todos.value = todos.value.filter((t) => t !== todo);
};

const deleteDone = (doneTodo) => {
  doneTodos.value = doneTodos.value.filter((t) => t !== doneTodo);
};
</script>

<style scoped></style> -->

<!-- <template>
  <div class="container p-5">
    <h4>My Todo Lists</h4>
    <div class="input-group w-50">
      <input type="text" v-model="inputTodo" class="form-control" />
      <button class="btn btn-primary" @click="addList">
        {{ editingTodo ? "Update" : "Add" }}
      </button>
    </div>

    <h5 class="mt-3">Todo List</h5>
    <ul>
      <li
        v-for="todo in todos"
        :key="todo.id"
        class="mt-3"
        @dblclick="markAsDone(todo)"
        title="double click"
      >
        <span style="cursor: pointer">{{ todo.name }}</span>
        <button class="btn btn-sm btn-success mx-2" @click="markAsDone(todo)">
          Done
        </button>
        <button class="btn btn-sm btn-warning mx-2" @click="editTodo(todo)">
          Edit
        </button>
        <button class="btn btn-sm btn-danger" @click="deleteTodo(todo)">
          Delete
        </button>
      </li>
    </ul>

    <h5 class="mt-5">Done List</h5>
    <ul>
      <li
        v-for="doneTodo in doneTodos"
        :key="doneTodo.id"
        @dblclick="markAsUndone(doneTodo)"
      >
        <span style="cursor: pointer">{{ doneTodo.name }}</span>
        <button
          class="btn btn-sm btn-warning border mx-2"
          @click="markAsUndone(doneTodo)"
        >
          Undone
        </button>
        <button
          class="btn btn-sm btn-danger border"
          @click="deleteDone(doneTodo)"
        >
          Delete
        </button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from "vue";

const Id = Math.floor(Math.random() * 10) + 1;
const todos = ref([]);
const doneTodos = ref([]);
const inputTodo = ref("");
const editingTodo = ref(null);

const addList = () => {
  if (inputTodo.value !== "") {
    if (editingTodo.value) {
      // Update existing todo
      editingTodo.value.name = inputTodo.value;
      editingTodo.value = null;
    } else {
      // Add new todo
      const newTodo = {
        id: Id,
        name: inputTodo.value,
        done: false,
      };
      todos.value.push(newTodo);
    }
    inputTodo.value = "";
  }
};

const markAsDone = (todo) => {
  todo.done = true;
  doneTodos.value.push(todo);
  todos.value = todos.value.filter((t) => t !== todo);
};

const markAsUndone = (doneTodo) => {
  doneTodo.done = false;
  todos.value.push(doneTodo);
  doneTodos.value = doneTodos.value.filter((t) => t !== doneTodo);
};

const deleteTodo = (todo) => {
  todos.value = todos.value.filter((t) => t !== todo);
};

const deleteDone = (doneTodo) => {
  doneTodos.value = doneTodos.value.filter((t) => t !== doneTodo);
};

const editTodo = (todo) => {
  editingTodo.value = todo;
  inputTodo.value = todo.name;
};
</script>

<style scoped></style> -->
