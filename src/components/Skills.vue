<template>
  <div class="container">
    <div class="holder">
      <form @submit.prevent="addSkill">
        <input
          v-validate="{rules: {min:5, max: 15}}"
          name="skill"
          type="text"
          placeholder="Enter a skill you have.."
          v-model="skill"
        >
        <transition
          name="alert-in"
          enter-active-class="animated flipInX"
          leave-active-class="animated flipOutX"
        >
          <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
        </transition>
      </form>
      <ul>
        <li v-for="(data, index) in skills" :key="index">{{data.skill}}
             <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
        </li>
      </ul>
      <p>These are the skills that you possess.</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Skills",

  data() {
    return {
      skill: "",
      skills: [
        { skill: "Vue" },
        { skill: "Fronetend Dev" },
        { skill: "UI Designer" }
      ]
    };
  },

  methods: {
    addSkill() {
      this.$validator.validateAll().then(result => {
        if (result) {
          console.log("addSkill: " + this.skill);
          this.skills.push({ skill: this.skill });
          this.skill = "";
        } else {
          console.log("Not valid");
        }
      });
    },

    remove(index) {
      this.skills.splice(index, 1);
    }
  }
};
</script>

<style src="./Skills.css" scoped></style>
