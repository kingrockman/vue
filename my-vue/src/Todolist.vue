<template>
  <div>
    <input @keyup.enter="cus_add" v-model="mycus" type="text" />
    <button @click="cus_add">添加</button>
    <table>
      <thead>
        <tr>
          <td>
            <input @change="ck_all" type="checkbox"/>
          </td>
          <td>编号</td>
          <td>名称</td>
          <td>地址</td>
          <td>操作</td>
        </tr>
      </thead>
      <tbody :key="i" v-for="(cus,i) in customers">
        <tr>
          <td>
            <input type="checkbox" />
          </td>
          <td>{{cus.number}}</td>
          <td>{{cus.name}}</td>
          <td>{{cus.address}}</td>
          <td>
            <a @click="cus_update(i)" href="javascript:;">修改</a>
            <a @click="cus_delete(i)" href="javascript:;">删除</a>
          </td>
        </tr>
      </tbody>
    </table>
    <p>{{customers.length}}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mycus: "",
      customers: [
        {
          number: "KH001",
          name: "晨希",
          address: "市区"
        },
        {
          number: "KH001",
          name: "晨希",
          address: "市区"
        }
      ]
    };
  },
  methods: {
    cus_add() {
      if (this.mycus === "") return;
      this.customers.push({
        number: "KH001",
        name: this.mycus,
        address: "市区"
      });
      this.mycus = "";
    },
    cus_update(i) {
      console.log("正在修改" + this.customers[i].name);
    },
    cus_delete(i) {
      this.customers.splice(i, 1);
    },
    ck_all(){
      console.log(this)
    }
  }
};
</script>

<style>
li.done {
  text-decoration: line-through;
  color: red;
}
</style>
