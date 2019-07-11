<template>
  <v-flex xs10 offset-xs1 md6 offset-md3 lg4 offset-lg4>
    <v-card class="title-card" @keyup.enter="onGuess">
      <v-card-title>
        <h1 display-4>SIAAAAAM</h1>
      </v-card-title>
      <v-card-text>
        <v-tooltip top>
          <template v-slot:activator="{ on }">
            <span class="font-italic font-weight-light" v-on="on">How many A's are in Siaaaaam?</span>
          </template>
          <span>Who knows?</span>
        </v-tooltip>

        <v-tooltip right>
          <template v-slot:activator="{ on }">
            <v-layout justify-center>
              <v-text-field v-model="guess" class="guess-input" xs4 offset-xs4 v-on="on" :error-messages="errors"></v-text-field>
            </v-layout>
          </template>
          <span>Take your guess!</span>
        </v-tooltip>

        <v-btn class="guess-button" @click="onGuess" color="info">Guess</v-btn>
      </v-card-text>
    </v-card>
  </v-flex>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      correct: String(Math.floor((new Date() - new Date(2017, 7, 24)) / 86400000)),
      guess: '',
      errors: [],
      messages: ['Really?', 'You\'re pretty far off', 'Do you even know Siaaaaam?', 'Try Again!', 'Your guess... is wrong', 'Just count the A\'s', 'Ask James - he probably knows', 'I\'m not going to tell you...']
    }
  },
  methods: {
    onGuess() {
      if (!this.guess.match(/^\d+$/)) {
        this.errors = ['Enter a postitive integer!']
      }
      else {
        if (this.guess !== this.correct) {
          const lastError = this.errors[0];
          let error = ''
          do {
            error = this.messages[Math.floor(Math.random() * this.messages.length)]
          } while (error === lastError)
          this.errors = [error]
        }
        else {
          this.$router.push('/siaaaaam')
        }
      }
    }
  },
  created() {

  }
}
</script>

<style scoped lang="sass">
.title-card
  h1
    text-align: center
    width: 100%
    font-size: 400%
  
  span
    font-size: 150%

  .guess-input
    max-width: 200px
  
  .guess-button
    margin-top: 20px

  margin-top: 100px
  text-align: center
</style>