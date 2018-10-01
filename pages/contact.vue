<template>
  <div class="contactContainer">
    <form id="contactForm">
      <ul>
        <li>
          <label>First name</label>
          <input type="text" v-model="contactForm.fName.value" v-on:keyup="validation">
          <div class="errorMessage">{{contactForm.fName.errors[0]}}</div>
        </li>
        <li>
          <label>Last name</label>
          <input type="text" v-model="contactForm.lName.value" v-on:keyup="validation">
          <div class="errorMessage">{{contactForm.lName.errors[0]}}</div>
        </li>
        <li>
          <label>Email</label>
          <input type="email" v-model="contactForm.email.value" v-on:keyup="validation">
          <div class="errorMessage">{{contactForm.email.errors[0]}}</div>
        </li>
        <li>
          <label>Message</label>
          <textarea type="text" v-model="contactForm.message.value" v-on:keyup="validation"></textarea>
          <div class="errorMessage">{{contactForm.message.errors[0]}}</div>
        </li>
        <li>
          <button v-on:click.prevent="sendFormData" id="contactBtn" name="contact" type="submit" class="btn btn-info">Submit</button>
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
      contactForm: {
        fName: {
          value: null,
          errors: []
        },
        lName: {
          value: null,
          errors: []
        },
        email: {
          value: null,
          errors: []
        },
        message: {
          value: null,
          errors: []
        }
      },
      errorsBool: null,
      successFail: null
    }
  },
  methods: {
    validation: function (e) {
      this.errorsBool = false;
      this.contactForm.email.errors = [];
      this.contactForm.fName.errors = [];
      this.contactForm.lName.errors = [];
      this.contactForm.message.errors = [];

      if (!this.contactForm.email.value) {
        this.contactForm.email.errors.push("Email required.");
      }

      if (!this.contactForm.fName.value) {
        this.contactForm.fName.errors.push("First name required.");
      }
      if (!this.contactForm.lName.value) {
        this.contactForm.lName.errors.push("Last name required.");
      }
      if (!this.contactForm.message.value) {
        this.contactForm.message.errors.push("Message required.");
      }

      var emailRegex = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;

      if (!emailRegex.test(this.contactForm.email.value)) {
        this.contactForm.email.errors.push("Invalid email format.");
      }

      for (var x in this.contactForm) {
        if (this.contactForm[x].errors.length > 0) {
          this.errorsBool = true;
        }
      }
    },
    sendFormData: function (e) {
      this.validation();
      if (!this.errorsBool) {
        db.collection("contactMessages").add({
          firstName: this.contactForm.fName.value,
          lastName: this.contactForm.lName.value,
          email: this.contactForm.email.value,
          message: this.contactForm.message.value
        })
          .then(data => {
            this.successFail = 'success'
            this.successFailMessage = "Message sent successfully."
            this.clearFields(this.contactForm)
          })
          .catch(error =>
            setTimeout(function () {
              this.successFail = 'fail',
                this.successFailMessage = "Failed. Please try again later."
            }, 1000)
          )
        e.preventDefault()
      }
    },
    clearFields: function (fields) {
      fields.fName.value = ''
      fields.lName.value = ''
      fields.email.value = ''
      fields.message.value = ''
    }
  }
}
</script>

<style>
.contactContainer {
  margin: auto;
  margin-bottom: 50px;
  width: 40%;
  background-color: hsla(0, 0%, 68%, 0.1);
}
#contactForm {
  padding: 20px;
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
input,
textarea {
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
