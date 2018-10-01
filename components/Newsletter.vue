<template>
  <div class="newsletterContainer">
    <form id="newsletterForm">
      <ul>
        <li>
          <label>Newsletter (enter email address)</label>
          <input type="email" v-model="newsletter.email.value" v-on:keyup="validation">
          <div class="errorMessage">{{newsletter.email.errors[0]}}</div>
        </li>
        <li>
          <button v-on:click.prevent="newsletterSignUp" id="contactBtn" type="submit" class="btn btn-info">Sign Up</button>
        </li>
        <div :class="successFail">{{successFailMessage}}</div>
      </ul>
    </form>
  </div>
</template>

<script>
import db from "../firestore/firebaseInit"

export default {
  data() {
    return {
      newsletter: {
        email: {
          value: null,
          errors: []
        }
      },
      errorsBool: null,
    }
  },
  methods: {
    validation: function (e) {
      this.errorsBool = false;
      this.newsletter.email.errors = [];

      if (!this.newsletter.email.value) {
        this.newsletter.email.errors.push("Email required.");
      }

      var emailRegex = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;

      if (!emailRegex.test(this.newsletter.email.value)) {
        this.newsletter.email.errors.push("Invalid email format.");
      }

      for (var x in this.newsletter) {
        if (this.newsletter[x].errors.length > 0) {
          this.errorsBool = true;
        }
      }
    },
    newsletterSignUp: function (e) {
      this.validation();
      if (!this.errorsBool) {
        db.collection("newsletter").add({
          email: this.newsletter.email.value
        })
          .then(data => {
            this.successFail = 'success'
            this.successFailMessage = "Successfully signed up"
            this.clearFields(this.newsletter)
          })
          .catch(error =>
            setTimeout(function () {
              this.successFail = 'fail',
                this.successFailMessage = "Failed. Please try later"
            }, 1000)
          );
        e.preventDefault()
      }
    },
    clearFields: function (fields) {
      fields.email.value = ''
    }
  }
}
</script>

<style>
.newsletterContainer {
  margin: auto;
  width: 40%;
  background-color: hsla(0, 0%, 68%, 0.1);
  margin: 30px;
}
#newsletterForm {
  padding: 0 20px;
}
ul {
  padding-left: 0;
}
li {
  list-style: none;
  padding: 10px;
  display: flex;
  flex-direction: column;
}
input {
  max-width: 100%;
  background-color: hsla(0, 0%, 68%, 0.1);
  outline-width: 0;
  border: none;
  min-height: 50px;
  font-size: 2em;
  color: inherit;
  padding-left: 15px;
}
label {
  font-size: 2em;
}
button {
  background-color: #c6c6c6;
  border: none;
  font-size: 2.5em;
  height: 50px;
  margin-top: 20px;
  width: 50%;
  margin: auto;
}
.errorMessage {
  color: red;
  font-size: 2em;
  text-align: right;
}
.success {
  color: green;
  font-size: 2em;
}
.fail {
  color: red;
  font-size: 2em;
}
</style>
