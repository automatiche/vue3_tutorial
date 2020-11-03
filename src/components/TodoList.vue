<template>
  <div class='container'>
    <h1>todolist</h1>
    <h3>未完成的列表</h3>
    <ul>
      <li class="list-group-item" v-for='(item, index) in lists' :key='index' @click='()=>(item.checked = !item.checked)'>
        <div class="form-group form-check">
          <input type="checkbox" class="form-check-input" :id="'item-' + index"
          v-model="item.checked"
          >
          <label class="form-check-label" :for="'item-' + index">{{item.name}}</label>
        </div>
      </li>
    </ul>
    <h3>已完成的列表</h3>
  </div>
</template>

<script>
import {reactive, toRefs} from 'vue'

export default {
  name: 'Todolist',
  setup(){
    // 1 加入checkbox  -> checked
    // 2 统计哪些 checked -> finish 列表
    // 3 添加item  -> item数据结构 -> name, checked , isEdit
    // 4 双击进行编辑
    // 5 删除功能 -> 删除特定index的元素
    const state = reactive({
      lists: [
        {
          name: '1',
          checked: false,
          isEdit: false
        },
        {
        name: '2',
        checked: false,
        isEdit: false
        },{
          name: '3',
          checked: false,
          isEdit: false
        },
      ],
      // finish: computed(() => state.lists.filter((item)=>item.checked == true))
    })
    return toRefs(state)
  }
}
</script>