<template>
  <div>
    <button
      class="btn btn-primary btn-sm"
      v-if="isShow"
      @click="isShow = false"
    >
      +Tag
    </button>
    <input
      v-else
      v-focus
      type="text"
      style="width: 50px"
      v-model="valTag"
      @blur="isAddTags"
      @keydown.enter="isAddTags"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShow: true,
      valTag: ''
    }
  },
  directives: {
    focus: {
      inserted(el) {
        el.focus()
      }
    }
  },
  methods: {
    isAddTags() {
      this.isShow = true
      if (this.valTag.trim() !== '') {
        this.$emit('addTags', this.valTag)
      }
      this.valTag = ''
    }
  }
}
</script>

<style></style>
