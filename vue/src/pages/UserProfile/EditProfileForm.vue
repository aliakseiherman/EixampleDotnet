<template>
  <form>
    <md-card>
      <md-card-header data-background-color="blue">
        <h4 class="title">Edit Profile</h4>
        <p class="category">
          Complete your profile
          <b>(no functionality at present)</b>
        </p>
      </md-card-header>

      <md-card-content>
        <div class="md-layout">
          <div class="md-layout-item md-small-size-100 md-size-50">
            <md-field>
              <label>First Name</label>
              <md-input v-model="firstname" type="text"></md-input>
            </md-field>
          </div>
          <div class="md-layout-item md-small-size-100 md-size-50">
            <md-field>
              <label>Last Name</label>
              <md-input v-model="lastname" type="text"></md-input>
            </md-field>
          </div>
          <div class="md-layout-item md-small-size-100 md-size-33">
            <md-field>
              <label>Email Address</label>
              <md-input v-model="emailadress" type="email"></md-input>
            </md-field>
          </div>
          <div class="md-layout-item md-size-100 text-right">
            <md-button disabled class="md-raised md-secondary">Update Profile</md-button>
          </div>
        </div>
      </md-card-content>
    </md-card>
  </form>
</template>
<script>
import { timeout } from "q";
import EventBus from "../../bus/event-bus";

export default {
  name: "edit-profile-form",
  props: {
    dataBackgroundColor: {
      type: String,
      default: ""
    }
  },
  data() {
    return {
      username: null,
      disabled: null,
      emailadress: null,
      lastname: null,
      firstname: null,
      address: null,
      city: null,
      country: null,
      code: null,
      aboutme:
        "Lamborghini Mercy, Your chick she so thirsty, I'm in that two seat Lambo."
    };
  },
  created() {
    let username = this.$store.getters.user
      ? this.$store.getters.user.userName
      : null;
    let firstname = this.$store.getters.user
      ? this.$store.getters.user.firstName
      : null;
    let lastname = this.$store.getters.user
      ? this.$store.getters.user.lastName
      : null;
    let email = this.$store.getters.user
      ? this.$store.getters.user.email
      : null;

    this.username = username;
    this.firstname = firstname;
    this.lastname = lastname;
    this.emailadress = email;

    EventBus.$emit("on-edit-profile-created", "lorem ipsum dolot sit amet..."); // demo
  }
};
</script>
<style></style>
