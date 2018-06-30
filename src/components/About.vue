<template>
	<div class="hello">
		<div class="holder">
			<h3>About Us</h3>
			<h4>{{ their_name }}</h4>
			<p>This is the about us section of this web app. This section is added just to showcase routing.</p>
		</div>
	</div>
</template>

<script>
export default {
  name: "Skills",
  data() {
    return {
		their_name: this.$route.params.name
    }
  }
}
</script>
