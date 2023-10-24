<template>
  <div class="ctr">
    <transition name="fade" mode="out-in">
      <questions 
        v-if="questionsAnswered < questions.length"
        :questions="questions"
        :questionsAnswered="questionsAnswered"
        @question-answered="questionAnswered"
      ></questions>
      <result v-else
        :results="results"
        :totalCorrect="totalCorrect"
      ></result>
    </transition>

    <button type="button" class="reset-btn" 
      @click.prevent="reset"
      v-if="questionsAnswered === questions.length"
      >Reset</button>
  </div>
</template>

<script>
import Questions from './components/Questions.vue';
import Result from './components/Result.vue';

export default {
  name: 'App',
  components: {
    Questions,
    Result
  },

  data() {
    return {
      questionsAnswered: 0,
      totalCorrect: 0,
      questions: [
        {
          q: "Translate this simple Klingon phrase to English\: bortaS bIr jablu'DI'reH QaQqu' nay'",
          answers: [
            {
              text: 'Where is the bathroom',
              is_correct: false
            },
            {
              text: 'You are an idiot',
              is_correct: false
            },
            {
              text: 'Do you speak Klingon',
              is_correct: false
            },
            {
              text: 'Revenge is a dish best served cold',
              is_correct: true
            }
          ]
        },
        {
          q: 'What is the lineage of masters up to Ahsoka?',
          answers: [
            {
              text: 'Yoda, Count Dooku, Qui gon Jinn, Obiwan Kenobi, Anakin Skywalker',
              is_correct: true
            },
            {
              text: 'Yoda, Obiwan Kenobi, Yoda, Anakin Skywalker, Qui gon Jinn',
              is_correct: false
            },
            {
              text: 'Count Dooku,Yoda, Qui gon Jinn, Obiwan Kenobi, Anakin Skywalker',
              is_correct: false
            },
            {
              text: 'Yoda, Obiwan Kenobi, Qui gon Jinn, Anakin Skywalker, Count Dooku',
              is_correct: false
            }
          ]
        },
        {
          q: 'Who was the first comic book super hero?',
          answers: [
            {
              text: 'Spiderman',
              is_correct: false
            },
            {
              text: 'Shazam',
              is_correct: false
            },
            {
              text: 'Superman',
              is_correct: true
            },
            {
              text: 'Captain America',
              is_correct: false
            }
          ]
        },
        {
          q: 'How many teeth does Gollum have?',
          answers: [
            {
              text: '9',
              is_correct: false
            },
            {
              text: '8',
              is_correct: false
            },
            {
              text: '7',
              is_correct: false
            },
            {
              text: '6',
              is_correct: true
            },
          ]
        },
        {
          q: 'Who does Faramir marry?',
          answers: [
            {
              text: 'Arwen',
              is_correct: false
            },
            {
              text: 'Eowyn',
              is_correct: true
            },
            {
              text: 'Galadriel',
              is_correct: false
            },
            {
              text: 'Unknown',
              is_correct: false
            },
          ]
        },
        {
          q: 'How many Horcruxes does Voldemort make?',
          answers: [
            {
              text: '6',
              is_correct: false
            },
            {
              text: '7',
              is_correct: true
            },
            {
              text: '8',
              is_correct: false
            },
            {
              text: '9',
              is_correct: false
            },
          ]
        },
        {
          q: 'Where do Sherlock and John live?',
          answers: [
            {
              text: '221b Baker Street',
              is_correct: true
            },
            {
              text: '22b Baker Street',
              is_correct: false
            },
            {
              text: '212b Baker Street',
              is_correct: false
            },
            {
              text: '2b Baker Street',
              is_correct: false
            },
          ]
        },
        {
          q: 'What is the Doctor\'s home planet?',
          answers: [
            {
              text: 'Skaro',
              is_correct: false
            },
            {
              text: 'Mondas',
              is_correct: false
            },
            {
              text: 'Gallifrey',
              is_correct: true
            },
            {
              text: 'Vortis',
              is_correct: false
            },
          ]
        },
        {
          q: 'Which character does NOT die in the finale?',
          answers: [
            {
              text: 'Daenerys',
              is_correct: false
            },
            {
              text: 'Jorah',
              is_correct: true
            },
            {
              text: 'Cersei',
              is_correct: true
            },
            {
              text: 'The Hound',
              is_correct: false
            },
          ]
        },
        {
          q: 'Which of these characters is not Force-sensitive?',
          answers: [
            {
              text: 'Rey Skywalker',
              is_correct: false
            },
            {
              text: 'Luke Skywalker',
              is_correct: false
            },
            {
              text: 'Princess Leia',
              is_correct: false
            },
            {
              text: 'Han Solo',
              is_correct: true
            },
          ]
        },
      ],
      results: [
        {
          min: 0,
          max: this.questions_length - 1,
          title: "Try again!",
          desc: "You're kind of a geek. You're definitely into some fandoms, but not all of them. Maybe your geekiness is less mainstream!"
        },
        {
          min: this.questions_length,
          max: this.questions_length,
          title: "Wow, you're the king geek!",
          desc: "Maybe you should contemplate your life choices a bit.."
        }
      ]
    }
  },

  methods: {
    questionAnswered(is_correct) {
      if(is_correct) {
        this.totalCorrect++
      }
      this.questionsAnswered++
    },

    reset() {
      this.questionsAnswered = 0;
      this.totalCorrect = 0;
    }
  },

  computed: {
    questions_length() {
      return this.questions.length
    }
  }

}
</script>

<style>

</style>
