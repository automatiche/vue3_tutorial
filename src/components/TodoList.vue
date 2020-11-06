<template>
  <div class='container'>
    <h1>todolist</h1>
    <h3>共有<span class='text-primary'>{{lists.length}}</span>个任务,其中<span class='text-success'>{{finish.length}}</span>个已完成任务</h3>
    <h3>未完成的列表</h3>
    <ul>
      <template  v-for='(item, index) in lists'>
        <!-- 此处点击click修改checked状态的行为是否不推荐 -->
        <li class="list-group-item" :key='index' @click='()=>(item.checked = !item.checked)' v-if='!item.checked'>
          <div class="form-group form-check">
            <input type="checkbox" class="form-check-input" :id="'item-' + index"
            v-model="item.checked"
            >
            <label class="form-check-label" :for="'item-' + index">{{item.name}}</label>
          </div>
        </li>
      </template>
    </ul>
    <h3>已完成的列表</h3>
    <ul>
      <li class="list-group-item" v-for='(item, index) in finish' :key="'finished-' + index">
        <div class="form-group form-check">
          <input type="checkbox" class="form-check-input" :id="'finished-' + index"
          v-model="item.checked"
          disabled
          >
          <label class="form-check-label" :for="'finished-' + index">{{item.name}}</label>
        </div>
      </li>
    </ul>
    <h3>添加新的task</h3>
    <div class="form-group">
      <label for="add">添加</label>
      <input 
        type="text" 
        class="form-control" 
        id="add" 
        placeholder="添加新的tesk" 
        v-model='value'
        @keydown.enter='add'
      >
    </div>
    <button type="button" @click='add' class="btn btn-primary btn-lg btn-block">确定添加</button>
  </div>
</template>

<script>
import {reactive, toRefs, computed} from 'vue'

export default {
  name: 'Todolist',
  setup(){
    // 1 加入checkbox  -> checked
    // 2 统计哪些 checked -> finish 列表
    // 3 添加item  -> item数据结构 -> name, checked , isEdit
    // 4 双击进行编辑
    // 5 删除功能 -> 删除特定index的元素

    const add = () => {
      state.lists.push({
        name: state.value,
        checked: false,
        isEdit: false
      })
      state.value = ''
    }
    const state = reactive({
      value: '',
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
      finish: computed(() => state.lists.filter((item)=>item.checked == true)),
      add,
    })
    return toRefs(state)
  }
}
</script>