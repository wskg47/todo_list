<template>
  <div>
    <li>
      <label>
        <input
          type="checkbox"
          :checked="todo.completed"
          @click="changeCheck(todo.id)"
        />
        <span>{{ todo.title }}</span>
      </label>
      <button class="btn btn-danger" @click="deleteObj(todo.id)">删除</button>
    </li>
  </div>
</template>

<script>
export default {
  name: 'MyItem',
  props: ['todo'],
  data() {
    return {}
  },
  methods: {
    // 删除任务
    deleteObj(id) {
      this.$bus.$emit('delTodo', id)
    },
    //勾选or取消勾选一个todo
    changeCheck(id) {
      this.$bus.$emit('checkTodo', id)
    },
  },
}
</script>

<style scoped>
/*item*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}

li:hover button {
  display: block;
}
</style>