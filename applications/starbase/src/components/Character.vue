<template>
<div class="col-md-4" @click="switchCharacter">
  <div class="character-card">
    <div class="card-block">
      <h4 class="card-title">{{character.id}}</h4>
      <p class="card-text">User Id: {{character.userId}}</p>
      <p class="card-text">Title: {{character.title}}</p>
      <p class="card-text">Body: {{character.body}}</p>
    </div>
  </div>
</div>
</template>

<script>
export default {
  props: ['id'],
  data() {
    return {
      character: {}
    }
  },
  methods: {
    fetchCharacter(id) {
      fetch(`https://jsonplaceholder.typicode.com/posts/${id}`, {
        method: 'GET'
      })
        .then(response => response.json())
        .then(json => this.character = json)
    },
    switchCharacter() {
      let random_id = Math.floor(Math.random() * 9) + 1
      this.fetchCharacter(random_id)
    }
  },
  created() {
    this.fetchCharacter(this.id)
  }
}
</script>