<template>
  <div class="hello">
    <h1 class="iconfont  icon-smile"> 递归树</h1>
    <ul id="demo">
      <item class="item" :model="treeData">
      </item>
    </ul>
  </div>
</template>
<script>
console.log(this)
import item from './child.vue'
export default {
  created:()=>{console.log(this)},
  methods: {
  },
  components: { item },
  data() {
    return {
      b: "",
      treeData: {
        name: '蜂投网',
        children: [
          { name: '行政' },
          { name: '人事' },
          {
            name: '技术中心',
            children: [{
                name: '李工',
                children: [
                  { name: 'PHP组' ,
                    children:[
                    {name:'代绮'},
                    {name:'姚美美'}]},
                  { name: 'js组',
                   children:[
                   {name:"硕哥"},{name:"唐老师"},{name:'胖子'}]}
                ]
              },
              { name: '谭工' },
              { name: '龙工' },
              
            ]
          }
        ]
      }
    }
  }
}

</script>

作者：虚光
链接：https://juejin.im/post/5a314731f265da432d281a9a
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。