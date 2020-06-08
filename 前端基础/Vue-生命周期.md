### Vue初始化简介

***



1. new vue()初始化
2. 挂载$mount方法，自定义Render方法、template、el等生产render函数
3. 通过watcher监听数据变化

### Vue-生命周期简介

***

Vue实例开始创建、初始化数据、编译模板、挂载DOM和渲染、更新和渲染、卸载

1. beforeCreate() //创建前

2. Create() // 创建实例（DOM还为创建$el属性不可操作）

3. beforeMounted() //挂载前

4. mounted //Dom挂载,vm实例化完成，可以通过Vm.$el访问Dom元素

5. beforeupdate() // 更新前

6. update() //更新

7. beforeDestroy/destroy //卸载

> Vm实例

- Vm.$el: 获取Vue实例关联的Dom元素
- vm.$data: 获取Vue实例的data对象
- vm.$options : 获取Vue实例的自定义属性
- vm.$refs: 获取页面中所有含有ref属性的DOM元素



