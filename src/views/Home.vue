<template>
  <div class="home">
    <h2>Normal form with submit</h2>
    <form id="form-with-integrated-submit" action="/about" method="get">
      <div>
        <label for="name1">Your Name</label>
        <input id="name1" name="email" />
      </div>
      <div>
        <label for="email1">Your email address</label>
        <input id="email1" name="email" />
      </div>
      <button type="submit" name="submit" id="submit">Submit</button>
    </form>

    <h2>Form with external submit button</h2>
    <form id="form-with-external-submit" action="/about" method="get">
      <div>
        <label for="name2">Your Name</label>
        <input id="name2" v-model="name" />
      </div>
      <div>
        <label for="email2">Your email address</label>
        <input id="email2" v-model="email" />
      </div>
      <input type="hidden" :value="name" name="name" />
      <input type="hidden" :value="email" name="email" />
    </form>
    <form
      id="submitting-form"
      action="/about"
      method="get"
      @submit="submitExternalForm"
    >
      <input
        type="hidden"
        name="tripwire"
        value="this-should-never-be-submitted"
      />
      <button type="submit" name="submit-external" id="submit-external">
        Submit
      </button>
    </form>

    <h2>Submit button with hidden fields</h2>
    <form id="hidden-value-form" action="/about" method="get">
      <input type="hidden" :value="name" name="name" />
      <input type="hidden" :value="email" name="email" />
      <button type="submit" name="submit-values" id="submit-values">
        Submit
      </button>
    </form>

    <div v-show="name === 'showform'">
      <h2>Hidden Form</h2>
      <form id="hidden-submit-form" action="/about" method="get">
        <div>
          <label for="name3">Your Name</label>
          <input id="name3" name="email" />
        </div>
        <div>
          <label for="email3">Your email address</label>
          <input id="email3" name="email" />
        </div>

        <button type="submit" name="submit-values" id="submit-values">
          Submit
        </button>
      </form>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

/* global _paq */

export default {
  name: "Home",
  data() {
    return {
      name: "",
      email: "",
    };
  },
  methods: {
    submitExternalForm(e) {
      e.preventDefault();
      const formElement = document.getElementById("form-with-external-submit");
      _paq.push(["FormAnalytics::trackFormSubmit", formElement]);
      formElement.submit();
    },
  },
};
</script>

<style>
label {
  display: inline-block;
  width: 150px;
}

form {
  padding: 5px;
  margin: 30px 0 0 0;
  border: dotted blue 1px;
  position: relative;
}

form[id]:before {
  position: absolute;
  content: attr(id);
  color: blue;
  padding: 2px 3px;
  border: dotted blue 1px;
  top: -22px;
  left: -1px;
  background: white;
  height: 24px;
}
</style>
