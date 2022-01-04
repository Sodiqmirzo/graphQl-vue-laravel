<template>
	<button @click="handleClick">Add new</button>
	<pre>{{ users.data }}</pre>
</template>

<script>
import gql from "graphql-tag";
export default {
	data: () => ({
		users: [],
		user: null,
	}),
	apollo: {
		users: {
			query: gql`
				{
					users {
						data {
							name
							email
						}
					}
				}
			`,
		},
	},
	methods: {
		handleClick() {
			this.$apollo.mutate({
				// Query
				mutation: gql`
					mutation {
						createUser(
							name: "Sodikmirzo Sattorov"
							email: "mr.sodiqmirzosattorov17@gmail.com"
							password: "password"
						) {
							name
						}
					}
				`,
			});
		},
	},
};
</script>