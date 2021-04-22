<template lang="pug">
span.UI-Switcher-Wrap
	input(:class="getClasses" v-bind="input" v-model="valueComponent" :value="value" type="checkbox")
</template>

<script>
export default {
	name: "ui-switcher",
	computed: {
		valueComponent: {
			get() {
				return this.modelValue;
			},
			set(value) {
				return this.$emit('update:modelValue', value);
			}
		},
		typeClass() {
			if (this.theme === "radio") return "UI-Radio";
			if (this.theme === "checkbox") return "UI-Checkbox";
			return "UI-Switcher";
		},
		stateValidClass() {
			if(this.invalid === true) return this.typeClass + "_Invalid";
			return this.typeClass + "_valid";
		},
		getClasses() {
			return [this.typeClass, this.stateValidClass];
		},
		input() {
			return {
				value: this.value,
				type: this.type,
				name: this.name,
				checked: this.checked,
				disabled: this.disabled,
				required: this.required
			}
		}
	},
	emits: ['update:modelValue'],
	props: {
		modelValue: {

		},
		invalid: {
			type: Boolean,
			default: false
		},
		theme: {
			type: String,
			default: "switcher"
		},
		name: {
			type: String,
			required: true
		},
		checked: {
			type: Boolean
		},
		required: {
			type: Boolean,
			default: false
		},
		disabled: {
			type: Boolean,
			default: false
		}
	}
}
</script>

<style scoped lang="postcss">
@supports (appearance: none) {
	.UI-Radio, .UI-Checkbox, .UI-Switcher {
		appearance: none;
		box-sizing: border-box;
		width: 20px;
		height: 20px;
		padding: 4px;
		margin: 5px;
		border: 2px solid #08573a;
		box-shadow: 0 0 0 0 #16db93;
		cursor: pointer;
		color: transparent;

		&:hover {
			border-color: #10a46e;
		}

		&:focus {
			box-shadow: 0 0 0 3px #16db93;
			outline: none;
		}

		&::before {
			content: "";
			display: block;
			width: 8px;
			height: 8px;
			background: currentColor;
		}

		&:invalid,
		&_Invalid{
			box-shadow: 0 0 0 3px #f44336	;
			border-color: maroon;
		}

		&:checked {
			color: #16db93;
		}

		&:disabled {
			border-color: gray;
			filter: grayscale(100%);
			cursor: not-allowed;
		}
	}

	.UI-Switcher {
		width: 40px;
		border-radius: 10px;
		padding: 2px;
		color: #16db93;

		&::before {
			border-radius: 50%;
			width: 12px;
			height: 12px;
		}



		&:checked {
			background: #16db93;
			color: white;

			&::before {
				margin-left: 19px;
			}
		}
	}

	.UI-Checkbox {

	}

	.UI-Radio {
		border-radius: 50%;
		color: white;

		&::before {
			border-radius: 50%;
		}
	}
}
</style>