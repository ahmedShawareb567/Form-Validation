<template>
  <div>
    <section class="registerSec">
      <div class="container">
        <div class="row">
          <div class="col-2"></div>
          <div class="col-8">
            <form role action method="get" @submit.prevent="validateFunc()">
              <h2>Vailidation Form</h2>
              <div class="row">
                <div class="col-lg-6 col-md-6 col-12 form-group">
                  <input
                    type="text"
                    class="form-control"
                    placeholder="First Name"
                    v-model="firstname"
                    ref="firstname"
                  />
                </div>
                <div class="col-lg-6 col-md-6 col-12 form-group">
                  <input
                    type="text"
                    class="form-control"
                    placeholder="Last Name"
                    v-model="lastname"
                    ref="lastname"
                  />
                </div>
                <div class="col-12 form-group">
                  <input
                    type="text"
                    class="form-control"
                    placeholder="User Name (optional)"
                    v-model="username"
                    ref="username"
                  />
                </div>
                <div class="col-lg-8 col-md-8 col-12 form-group">
                  <input
                    type="text"
                    class="form-control"
                    placeholder="Mobile No (optional)"
                    v-model="mobileNo"
                    ref="mobileNo"
                  />
                </div>
                <div class="col-lg-4 col-md-4 col-12 form-group">
                  <input
                    type="text"
                    class="form-control"
                    placeholder="Zip Code (optional)"
                    v-model="zipcode"
                    ref="zipcode"
                  />
                </div>
                <div class="col-12 form-group">
                  <input type="Email" class="form-control" placeholder="Email" v-model="email" />
                </div>
                <div class="col-lg-6 col-md-6 col-12 form-group">
                  <input
                    type="password"
                    class="form-control"
                    placeholder="Password"
                    v-model="password"
                    ref="password"
                  />
                </div>
                <div class="col-lg-6 col-md-6 col-12 form-group">
                  <input
                    type="password"
                    class="form-control"
                    placeholder="Confirm Password"
                    v-model="confirmPassword"
                    ref="confirmPass"
                  />
                </div>
                <div class="col-12">
                  <div class="erroSec">
                    <ul>
                      <li v-for="(error, index) in error_arr" :key="index">
                        <p v-if="error_arr[index] != ''">
                          <i class="fa fa-close"></i>
                          {{error}}
                        </p>
                      </li>
                    </ul>
                  </div>
                </div>
                <div class="col-12 form-group">
                  <input type="submit" value="Register" />
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<script>
export default {
  created() {},
  mounted() {},
  updated() {},
  data() {
    return {
      firstname: "",
      lastname: "",
      username: "",
      email: "",
      password: "",
      confirmPassword: "",
      error_arr: []
    };
  },
  watch: {
    confirmPassword() {
      if (this.confirmPassword != this.password) {
        this.$refs.confirmPass.classList.add("error_class");
        this.error_arr[1] = "Not Matching";
        this.error_arr.splice(0, 1);
      } else {
        this.$refs.confirmPass.classList.remove("error_class");
        this.error_arr.splice(1, 1);
        this.error_arr.splice(0, 1);
      }
    },
    firstname() {
      if (this.firstname != "") {
        this.error_arr.splice(0, 1);
        this.$refs.firstname.classList.remove("error_class");
      } else {
        this.error_arr[0] = "Required ?!";
        this.$refs.firstname.classList.add("error_class");
      }
    },
    lastname() {
      if (this.lastname != "") {
        this.error_arr.splice(0, 1);
        this.$refs.lastname.classList.remove("error_class");
      } else {
        this.error_arr[0] = "Required ?!";
        this.$refs.lastname.classList.add("error_class");
      }
    },
    password() {
      if (this.password != "") {
        this.error_arr.splice(0, 1);
        this.$refs.password.classList.remove("error_class");
      } else {
        this.error_arr[0] = "Required ?!";
        this.$refs.password.classList.add("error_class");
      }
    }
  },
  methods: {
    validateFunc() {
      if (this.firstname == "") {
        this.$refs.firstname.focus();
        this.$refs.firstname.classList.add("error_class");
      } else {
        this.$refs.firstname.classList.remove("error_class");
      }

      if (this.lastname == "") {
        this.$refs.lastname.focus();
        this.$refs.lastname.classList.add("error_class");
      } else {
        this.$refs.lastname.classList.remove("error_class");
      }

      if (this.password == "") {
        this.$refs.password.focus();
        this.$refs.password.classList.add("error_class");
      } else {
        this.$refs.password.classList.remove("error_class");
      }

      if (this.confirmPassword == "") {
        this.$refs.confirmPass.focus();
        this.$refs.confirmPass.classList.add("error_class");
      } else {
        this.$refs.confirmPass.classList.remove("error_class");
      }
    }
  }
};
</script>
