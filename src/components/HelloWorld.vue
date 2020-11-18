<template>
  <div id="example-one" class="container mb-3 mt-3">
    <h1>vue-form-json-schema</h1>
    <h3>
      Example #1
      <small class="text-muted">Minimal example</small>
    </h3>
    <p class="lead">
      <span>
        A minimal example showing a simple
        <code>input</code> field.
      </span>
    </p>
    <p class="text-center font-weight-bold">
      <a
        href="https://codesandbox.io/s/py6611pr9m"
        target="_blank"
        rel="noopener noreferrer"
        >Click here to edit this demo</a
      >
    </p>
    <p class="text-center font-weight-bold">
      <a
        href="https://py6611pr9m.codesandbox.io/"
        target="_blank"
        rel="noopener noreferrer"
        >Click here to show this demo in a separate window</a
      >
    </p>

    <vue-form-json-schema
      v-model="model"
      :schema="schema"
      :ui-schema="uiSchema"
      v-on:state-change="onChangeState"
      v-on:validated="onValidated"
    ></vue-form-json-schema>

    <hr />
  </div>
</template>

<script>
// Import VueFormJsonSchema
import VueFormJsonSchema from "vue-form-json-schema/dist/vue-form-json-schema.esm.js";
// We use a component to display JSON in a pretty way
// it is NOT included NOR required by VueFormJsonSchema
export default {
  name: "example-one",
  components: {
    "vue-form-json-schema": VueFormJsonSchema,
  },
  data() {
    return {
      model: {},
      state: {},
      valid: false,
      schema: {
        type: "object",
        properties: {
          firstName: {
            type: "string",
          },
        },
      },
      uiSchema: [
        {
          component: "input",
          model: "firstName",
          fieldOptions: {
            class: ["form-control"],
            on: ["input"],
            attrs: {
              placeholder: "Please enter your name",
            },
          },
        },
      ],
    };
  },
  methods: {
    onChangeState(value) {
      this.state = value;
    },
    onValidated(value) {
      this.valid = value;
    },
  },
};
</script>