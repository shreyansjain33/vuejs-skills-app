<template>
	<div class="hello">
		<div class="holder">
			<form @submit.prevent="addSkill">
				<input type="text"
					placeholder="Enter a skill that you have.."
					v-model="item"
					v-validate="'min:5,'"
					name="item"
				>
				<transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
					<p class="alert" v-if="errors.has('item')">{{ errors.first('item') }}</p>
				</transition>
			</form>
			<h3>My Skills <span class="pull-right"> [ {{ skills.length }} ]</span></h3>
			<ul>
				<transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
					<li v-for="(data, index) in skills" :key="index">{{index}}. {{ data.skill }}
						<span class="fa" v-on:click="remove(index)"></span>
					</li>
				</transition-group>
			</ul>
		</div>
	</div>
</template>

<script>
export default {
  name: "Skills",
  data() {
    return {
      item: "",
      skills: [
        { skill: "Vue.JS" },
        { skill: "Angular JS" },
        { skill: "React JS" }
      ]
    };
  },
  methods: {
    addSkill() {
		this.$validator.validateAll().then((result) => {
			if(result){
				this.skills.push({ skill: this.item });
				this.item = '';
			} else {
				console.log("Data Invalid");
				this.item = '';
			}
		});
	},
	remove(id){
		this.skills.splice(id,1);
	}
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";

/* .hello {
  margin-left: 40%;
} */
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 1px 10px;
  padding: 10px;
  text-align: left;
  background: lightblue;
  border-left: 2px solid lightseagreen;
}
a {
  color: #42b983;
}
input {
  width: 100%;
  padding: 10px 10px 10px 15px;
}
.alert {
	font-weight: bold;
	display: inline-block;
	padding: 5px;
	margin-top: 5px;
}
span.fa::after {
	content: '-';
	font-size: 24px;
	margin-top: -5px;
	padding: 0 10px;
	border-radius: 50%;
	background: #222;
	color: #fff;
	float: right;
	cursor: pointer;
}
</style>
