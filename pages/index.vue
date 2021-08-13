<template>
  <div class="container">
    <h1 class="header">お薬かぞえくん</h1>
    <v-row>
      <v-col cols="6">
        <p class="title">1日量</p>
      </v-col>
      <v-col cols="6">
        <v-text-field
            label="1日量"
            v-model="dose"
          ></v-text-field>
      </v-col>
      <v-col cols="6">
        <p class="title">服用日数</p>
      </v-col>
      <v-col cols="6">
        <v-text-field
            label="服用日数"
            v-model="day"
          ></v-text-field>
      </v-col>
      <v-col cols="6" class="sample">
        <p class="title">1シートの錠数</p>
      </v-col>
      <v-col cols="6">
        <v-text-field
            label="1シートの錠数"
            v-model="set"
          ></v-text-field>
      </v-col>

      <v-col class="text-center" cols="12">
        <v-btn class="button" @click="medicines(day, set, dose)">
          <p>決定</p>
        </v-btn>
      </v-col>
      <v-col>
        <p class="text-center font-bold answer">{{ answer }}</p>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      day: 0,
      set: 0,
      dose: 0,
      answer: ""
    }
  },
  methods: {
    medicines(day, set, dose) {
      let totalNumber = day * dose
      let decimalSet = totalNumber / set;
      let integerSet = Math.floor( decimalSet ) ;
      let totalSet = integerSet * set
      let Individual = totalNumber - totalSet
      this.answer = integerSet + "シートと" + Individual +"錠"
    }
  }
}
</script>

<style scoped>
  .container {
    max-width: 1000px;
  }
  .header {
    text-align: center;
    margin-bottom: 50px;
    margin-top: 30px;
  }
  .title {
    text-align: center;
    line-height: 60px;
  }
  .text-center {
    text-align: center;
  }
  .button {
    width: 50%;
  }
  .font-bold {
    font-weight: bold;
  }
  .answer {
    font-size: 25px;
  }
</style>