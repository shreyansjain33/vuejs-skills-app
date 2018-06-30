<template>
	<div class="hello">
		{{ name }}
		<br>
		{{ btnState ? 'Button Disabled' : 'Button Enabled' }}
		<button v-on:click="changeName" v-bind:disabled="btnState">Change Name</button>
		<hr>
		<div class="holder">
			<input type="text" placeholder="Enter a skill that you have.." v-model="item">
			{{ item }}

			<h3>My Skills <span class="pull-right"> [ {{ skills.length }} ]</span></h3>
			<ul>
				<li v-for="(data, index) in skills" :key="index">{{index}}) {{ data.skill }}</li>
			</ul>
			<p v-if="skills.length >= 2">OMG! So Skilled!</p>
			<p v-else>You need to work!</p>
		</div>
		<hr>
		<div v-bind:class="{ msg: btnState, 'msg-border': btnState }"></div>
		<hr>
	</div>
</template>

<script>
export default {
  name: "Skills",
  data() {
    return {
      item: "",
      name: "This is the interpolated message.",
      btnState: true,
      skills: [
        { skill: "Vue.JS" },
        { skill: "Angular JS" },
        { skill: "React JS" }
      ]
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
  margin-left: 44%;
}
li {
  margin: 0 10px;
  text-align: left;
}
a {
  color: #42b983;
}
.msg {
  background: green;
  min-height: 30px;
}
.msg-border {
  transition: all ease-in 0.4s;
  box-shadow: 0 0 15px 2px rgba(0, 0, 0, 0.4);
}
.msg-border:hover {
  transition: all ease-in 0.4s;
  box-shadow: 0 0 6px 0 rgba(0, 0, 0, 0.2);
}
</style>
