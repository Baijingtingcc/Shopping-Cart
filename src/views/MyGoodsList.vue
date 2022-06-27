<template>
  <div>
    <my-table :goodsList="goodsList">
      <template #main>
        <th>#</th>
        <th>商品名称</th>
        <th>价格</th>
        <th>标签</th>
        <th>操作</th>
      </template>

      <template #curr="{ item }">
        <td>{{ item.id }}</td>
        <td>{{ item.goods_name }}</td>
        <td>{{ item.goods_price }}</td>
        <td>
          <addTags @addTags="addTags(item.tags, $event)" />
          <span
            class="badge bg-warning text-dark"
            v-for="(i, index) in item.tags"
            :key="index"
            style="margin-right: 5px"
            >{{ i }}</span
          >
        </td>
        <td>
          <button class="btn btn-danger btn-sm" @click="delTags(item.id)">
            删除
          </button>
        </td>
      </template>
    </my-table>
  </div>
</template>

<script>
import addTags from '@/views/addTags.vue'
import MyTable from '@/components/MyTable.vue'
import axios from '@/utils/request.js'
export default {
  components: {
    MyTable,
    addTags
  },
  data() {
    return {
      goodsList: []
    }
  },
  created() {
    this.getGoodsList()
  },
  methods: {
    async getGoodsList() {
      const { data } = await axios({ url: '/api/goods' })
      this.goodsList = data.data
    },
    delTags(id) {
      this.goodsList = this.goodsList.filter((item) => item.id !== id)
    },
    addTags(tags, valTag) {
      tags.push(valTag)
    }
  }
}
</script>

<style></style>
