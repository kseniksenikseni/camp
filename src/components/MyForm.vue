<template>
  <form @submit.prevent v-if="statusUser">
    <input placeholder="Напишите отзыв..." v-model="form.feedback">
    <my-button class="btn-add" @click="addFeed">Отправить</my-button>
  </form>
</template>

<script>
import MyButton from "@/components/MyButton";
export default {
  components: {MyButton},
  props: {
    statusUser: {
      type: Boolean,
      default: false
    },
    data() {
      return {
        form: {
          feedback: ''
        }
      }
    },
    methods: {
      addFeed() {
        this.form.id = Date.now()
        this.$emit('create', this.form)
        this.form = {
          feedback: ''
        }
      }
    }
  }
}
</script>

<style scoped>
input{
  width: 300px;
  height: 50px;
}
</style>