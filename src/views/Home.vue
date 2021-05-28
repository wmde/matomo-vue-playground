<template>
  <div class="home">
    <h2>Choice Form:</h2>
    <form id="choice" class="choiceForm">
      <label>
        <input type="radio" name="formtype" value="a" v-model="formtype" />
        Form type A</label
      >
      <label>
        <input type="radio" name="formtype" value="b" v-model="formtype" />
        Form type B</label
      >
      <label>
        <input type="radio" name="formtype" value="c" v-model="formtype" />
        Form type C</label
      >
    </form>
    <div class="displayFormId">
      Current Matomo form id: <code>dynamic-form-{{ formtype }}</code>
    </div>
    <h2>Dynamic Form</h2>
    <form :id="`dynamic-form-${formtype}`" class="dynamicForm" action="/about">
      <div>Shared input on all form types: <input name="name" /></div>
      <div v-if="formtype == 'a'">
        Special input on type A: <input name="special" />
      </div>
      <div v-if="formtype == 'b'">
        Special input on type B: <input name="special" />
      </div>
      <div v-if="formtype !== 'unset'">
        <button type="submit">Submit</button>
      </div>
      <div v-else>Please select a form type</div>
    </form>
  </div>
</template>

<script>
// @ is an alias to /src

/* global _paq */

export default {
  name: "Home",
  data() {
    return {
      formtype: "unset",
    };
  },
  watch: {
    formtype: function (oldFormtype, newFormtype) {
      console.log("Form type changed", oldFormtype, newFormtype);
      if (typeof _paq !== "undefined") {
        // scan on every change, just to be sure Matomo picks up the new form id
        console.log("Triggering form scan ...");
        _paq.push(["FormAnalytics::scanForForms"]);
      }
    },
  },
};
</script>

<style>
.choiceForm label {
  display: block;
}

.displayFormId {
  padding: 2em;
  background: lightgrey;
  margin: 2em 0;
}
.dynamicForm div {
  margin-bottom: 1em;
}
code {
  font-weight: bold;
}
</style>
