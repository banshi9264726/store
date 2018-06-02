<template>
  <div>
    <h2 class="sub-header">英雄修改</h2>
    <form>
          <div class="form-group">
            <label for="name">英雄姓名</label>
            <input v-model="formData.name" type="text" class="form-control" id="name" value="">
          </div>
          <div class="form-group">
            <label for="gender">英雄性别</label>
            <input v-model="formData.gender" type="text" class="form-control" id="gender" value="">
          </div>
          <button type="submit" class="btn btn-success" @click.prevent="handleEdit">Submit</button>
        </form>
  </div>
</template>

<script>

export default {
  data() {
    return {
      formData: {
        name: '',
        gender: ''
      },
      id: -1
    };
  },
  created() {
    // 获取url上的参数
    this.id = this.$route.params.id;
    this.loadData();
  },
  methods: {
    loadData() {
      // 发送请求获取当前要编辑的英雄对象
      this.$http.get(`/heroes/${this.id}`)
        .then((res) => {
          if (res.status === 200) {
            this.formData = res.data;
          }
        })
        .catch((error) => {
          console.log(error);
        });
    },
    handleEdit() {
      this.$http.patch(`/heroes/${this.id}`, this.formData)
        .then((res) => {
          // 修改成功
          this.$router.push({
            name: 'heroes'
          });
        })
        .catch((error) => {
          console.log(error);
        });
    }
  }
};
</script>

<style>

</style>
