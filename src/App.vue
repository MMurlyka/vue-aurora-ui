<template lang="pug">
.App
	.Grid
		label.Grid-Col
			ui-checkbox(name="checkbox1" checked theme="checkbox" required :invalid="!checkbox1" v-model="checkbox1")
			| {{checkbox1 ? 'YES' : 'NO'}}
		.Grid-Col
			ui-checkbox(name="checkbox2" theme="checkbox" v-model="checkbox2")
			| {{checkbox2 ? 'YES' : 'NO'}}
		.Grid-Col
			ui-checkbox(name="checkbox3" theme="checkbox" checked disabled v-model="checkbox3")
			| {{checkbox3 ? 'YES' : 'NO'}}
		.Grid-Col
			ui-checkbox(name="checkbox4" theme="checkbox" disabled v-model="checkbox4")
			| {{checkbox4 ? 'YES' : 'NO'}}

		.Grid-Col
			ui-checkbox(name="radio" theme="radio" v-model="radio1" :checked="true")
			| {{radio1 ? 'YES' : 'NO'}}
		.Grid-Col
			ui-checkbox(name="radio" theme="radio" v-model="radio2" value="Two")
			| {{radio2 ? 'YES' : 'NO'}}
		.Grid-Col
			ui-checkbox(name="dradio" theme="radio" disabled v-model="radio3" value="One")
			| {{radio3 ? 'YES' : 'NO'}}
		.Grid-Col
			ui-checkbox(name="dradio" theme="radio" disabled v-model="radio4" value="Two")
			| {{radio4 ? 'YES' : 'NO'}}

		.Grid-Col
			ui-checkbox(name="switcher" theme="switcher" v-model="switcher1" checked)
			| {{switcher1 ? 'YES' : 'NO'}}
		.Grid-Col
			ui-checkbox(name="switcher" theme="switcher" v-model="switcher2")
			| {{switcher2 ? 'YES' : 'NO'}}
		.Grid-Col
			ui-checkbox(name="switcher" theme="switcher" disabled checked v-model="switcher3")
			| {{switcher3 ? 'YES' : 'NO'}}
		.Grid-Col
			ui-checkbox(name="switcher" theme="switcher" disabled v-model="switcher4")
			| {{switcher4 ? 'YES' : 'NO'}}
</template>

<script>
import UiCheckbox from "@/components/UICheckbox.vue";

export default {
	name: 'App',
	data() {
		return {
			checkbox1: false,
			checkbox2: true,
			checkbox3: true,
			checkbox4: false,

			radio1: true,
			radio2: false,
			radio3:	true,
			radio4: false,

			switcher1: true,
			switcher2: false,
			switcher3: true,
			switcher4: false
		}
	},
	components: {
		UiCheckbox
	}
}
</script>

<style scoped lang="postcss">
.Grid {
	display: grid;
	width: 600px;
	grid-template-columns: repeat(4, 1fr);

	&-Col {
		padding: 25px;
	}
}
</style>
