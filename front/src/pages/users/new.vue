<template>
  <section>
    <div>
      <h1>New user</h1>
      <v-form @submit.prevent="post">
        <v-text-field
          v-model="name"
          label="氏名"
          type="text"
          >Name:
        </v-text-field>
        <v-btn
          type="submit"
          color="info"
          >submit
        </v-btn>
      </v-form>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      name: ''
    }
  },
  methods: {
    post() {
      this.$axios.post(
        '/api/users',
        {
          name: this.name
        }
      ).then((res) => {
        this.$router.push(`${res.data.id}`)
      })
    }
  }
}
</script>