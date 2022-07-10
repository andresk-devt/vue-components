<template>
  <div class="input-container" :class="inputClases">
    <input
      :id="id"
      class="input-content"
      :type="type"
      :required="required"
      :disabled="disabled"
      :label="label"
      v-model="input"
    />
    <label :for="id" class="input-label" >{{ label }}</label>
  </div>
</template>

<script>
export default {
  props: {
    type: {
      type: String,
      default: "text",
      required: true,
    },
    required: {
      type: Boolean,
      default: false,
      required: false,
    },
    disabled: {
      type: Boolean,
      default: false,
      required: false,
    },
    label: {
      type: String,
      required: true,
    },
    id: {
      type: String,
      default: 'input-content',
      required: true
    }
  },
  data() {
    return {
      input: null,
    };
  },
  computed: {
    inputClases() {
      return {
        'input-value': this.input
      }
    }
  },
  methods: {}
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Imprima&display=swap');

.input-container {
  position: relative;
}
.input-content {
  padding: 10px;
  width: 220px;
  border: none;
  border-radius: 4px;
  font-family: 'Imprima', sans-serif;
  color: black;
  background-color: transparent;
  outline: 1.8px solid #fff;
}
.input-label {
  position: absolute;
  top: 0;
  left: 0;
  transform: translate(8px, 8px);
  transition: transform 0.25s;
  font-family: 'Imprima', sans-serif;
}
.input-content:focus + .input-label,
.input:valid + .input-label {
  transform: translate(-12px, -20px) scale(0.8);
  color: black;
  padding-inline: 5px;
}
.input-content:is(:focus, :valid) {
  outline-color: black;
}
.input-value .input-label {
  transform: translate(-12px, -20px) scale(0.8);
  color: black;
  padding-inline: 5px;
}
</style>
