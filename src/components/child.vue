<template>
  <div class="hello">
  
    <div
      :class="{bold: isFolder}"
       @click="toggle"
       @dblclick="changeType">
      <img src="../assets/arrow-right.png"  v-if="isFolder" style="width: 1rem;transition: transform 0.5s" :style="{transform: ttt } ">
         {{model.name}}
    </div>
    <ul v-show="open" v-if="isFolder">
      <item
        class="item"
        v-for="(model,index) in model.children"
        :model="model"
        :key="index">
      </item>
      <li class="add" @click="addChild">+</li>
    </ul>
  
  </div>
</template>
<script>
export default {
  name: 'item',
 props: {
    model: Object
  },
  data: function () {
    return {
      open: false,
      ttt:'rotate(0deg)'
    }
  },
  computed: {
    isFolder: function () {
      return this.model.children &&
        this.model.children.length
    }
  },
  methods: {
    toggle: function () {
      if (this.isFolder) {
        if(this.ttt=="rotate(90deg)"){
        this.ttt='rotate(0deg)'
      }else{
        this.ttt='rotate(90deg)'
      }
      setTimeout(()=>{this.open = !this.open},50)
      }
    },
    changeType: function () {
      console.log(123)
      if (!this.isFolder) {
         console.log("db")
        this.$set(this.model, 'children', [])
        this.addChild()
        this.open = true
      }
    },
    addChild: function () {
      let a =prompt("请输入你的姓名","姓名")
      if(a){
      this.model.children.push({
        name: a
      })}
    }
  }
}
</script>