<script setup>
import CompanyLogo from './CompanyLogo.vue'

import { ref, computed } from 'vue'
//  all variables....here
const formData = ref({
  email: '',
  password: ''
})
const passwordHide = ref(true)
const passwordType = ref('password')
const newUserToggle = ref(false)
const isEmailValid = computed(() => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.value.email))
const isPasswordValid = computed(() => formData.value.password.length >= 8)
const isFormValid = computed(() => isEmailValid.value && isPasswordValid.value)

const submitForm = () => {
  if (!newUserToggle.value) {
    //  if user is old then run this code...
    if (isFormValid.value) {
      // if input is currect then run this code
      alert('Form submitted!', formData.value)
    } else {
      // else run this code...
      console.log('Form is invalid. Please check the fields.')
    }
  } else {
    if (isEmailValid.value) {
      // if user in new then run this code
      //  Send otp and create New User.. logic write here..
      alert('Send otp and create new user')
    }
  }
}
const passowrdVisibilityToggle = () => {
  // password visibility toggle (show / hide)
  passwordHide.value = !passwordHide.value
  passwordType.value = passwordHide.value ? 'password' : 'text'
}

const forgotPasswordLogic = () => {
  if (!newUserToggle.value) {
    // reset password logic write here....
    alert('Reset your password')
  } else {
    // reset your email id or phone number logic write here....
    alert('Reset your email id or phone number ')
  }
}

const newUserToggleBtn = () => {
  // toggel user.
  //  if user is old then change to new user
  newUserToggle.value = !newUserToggle.value
  formData.value.email = ''
  formData.value.password = ''
}
</script>

// HTML
<template>
  <div class="sign-in-component">
    <div class="sign-in-container">
      <CompanyLogo />
      <h6 class="sign-in-title">Sign in</h6>
      <form @submit.prevent="submitForm" class="custom-form">
        <div class="form-group email-f-g">
          <label for="Email">Email</label><br />

          <input
            v-model="formData.email"
            type="text"
            id="email"
            :placeholder="!newUserToggle ? 'Enter your email address' : 'Email or mobile number '"
            :class="isEmailValid ? '' : 'input-error'"
          />
          <span v-if="!isEmailValid" class="error">Please enter a valid email address</span>
        </div>

        <div v-if="!newUserToggle" class="form-group password-f-g">
          <label for="password">Password</label><br />
          <div class="ps-box">
            <input
              v-model="formData.password"
              :type="passwordType"
              id="password"
              placeholder="Enter your Password"
              :class="isPasswordValid ? '' : 'input-error'"
            />
            <div class="show-password" @click="passowrdVisibilityToggle">
              <i v-if="passwordHide" class="fa-solid fa-eye-slash"></i>
              <i v-else class="fa-solid fa-eye"></i>
            </div>
          </div>
          <span v-if="!isPasswordValid" class="error">Password must be at least 8 characters</span>
        </div>
        <div class="forgot-password-box">
          <a v-if="newUserToggle" @click="forgotPasswordLogic" class="forgot-password" href="#"
            >Forgot email or phone number?</a
          >
          <a v-else class="forgot-password" @click="forgotPasswordLogic" href="#"
            >Forgot Password?</a
          >
        </div>
        <div class="check-box-group">
          <input class="my-checkbox" type="checkbox" />
          <span>Keep me signed in for 30 days</span>
        </div>
        <button class="btn sign-in-Button">
          {{ !newUserToggle ? 'SIGN IN' : 'Send Sign-in code' }}
        </button>
        <p class="or-text">OR</p>
        <button class="btn sign-in-code-button" @click="newUserToggleBtn">
          {{ !newUserToggle ? 'Use a sign-in code' : 'Use Password' }}
        </button>
      </form>
    </div>
    <div class="sign-in-footer">
      <div class="company-services">
        <p>Read our Terms of Service <i class="fa-solid fa-arrow-up-right-from-square"></i></p>
      </div>
      <div class="our-partners">
        <p class="footer-title">OTHER WAYS TO WATCH</p>
        <ul>
          <li><img src="../../public/appTv.svg" alt="" /></li>
          <li><img src="../../public/isoicon.svg" alt="" /></li>
          <li><img src="../../public/roku.svg" alt="" /></li>
          <li><img src="../../public/amazonicon.svg" alt="" /></li>
        </ul>
        <p class="other-app-title">Search for AppleTV+ FYC on your App Store</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
:root {
  --mobile-label: '17px';
  --blue-color: '#0057ff';
}
.sign-in-component {
  width: 556px;
  height: 900px;
  border-radius: 15px;
  background-color: aliceblue;
  margin: auto;
  box-shadow: inset 0px 0px 5px 3px #181818;
  background-color: #0a0a0aeb;
  color: white;
  position: relative;
}
.sign-in-container {
  padding: 10px 64px 0 64px;
}
.sign-in-title {
  font-size: 26px;
  font-family: 'Noto Sans', sans-serif;
  font-weight: 500;
}
.form-group {
  margin-top: 18px;
  /* background-color: darkblue; */
}
label {
  color: #1a68ff;
  font-size: 19px;
  font-weight: 500;
}
.input-error {
  box-shadow: inset 0px 0px 4px 1px #ff4848;
  border: none;
}

.error {
  color: #ff4848;
  margin-top: 9px;
  position: relative;
  padding-left: 20px;
}
.error::before {
  content: url('../../public/cross.svg');
  padding: 6px;
  align-items: center;
  width: 15px;
  top: -5px;
  left: 18px;
  transform: translateX(-20px);
  position: absolute;
}
.ps-box {
  position: relative;
}
.show-password {
  position: absolute;
  border: none;
  top: 30px;
  right: 0;
  transform: translateX(-20px);
  width: 25px;
}
.show-password > i {
  color: rgba(255, 255, 255, 0.632);
  font-size: 15px;
}
.password-f-g {
  margin-top: 15px;
}

.forgot-password-box {
  margin-top: 15px;
  text-align: right;
}
.forgot-password {
  text-decoration: none;
  color: #ffffff;
  font-size: 19.5px;
}

.check-box-group {
  margin-top: 9px;
  height: 30px;
  display: flex;
  align-items: center;
}

.my-checkbox {
  width: 25px;
  border: none;
  position: relative;
}
input[type='checkbox'] {
  appearance: none;
  -webkit-appearance: none;
  height: 27px;
  background-color: #d5d5d500;
  border: 1.5px solid rgba(255, 255, 255, 0.594);
  border-radius: 5px;
  cursor: pointer;
}
input[type='checkbox']:after {
  font-family: 'Font Awesome 5 free ';
  font-weight: 900;
  content: '✔';
  font-size: 20px;
  color: rgba(255, 255, 255, 0.786);
  position: absolute;
  top: -5px;
  right: 5px;
  display: none;
}
input[type='checkbox']:hover {
  background-color: #a5a5a5;
}
input[type='checkbox']:checked {
  background-color: #0057ff;
}
input[type='checkbox']:checked:after {
  display: block;
}
.check-box-group span {
  margin-top: 10px;
  padding-left: 6px;
  color: #bcbcbc;
  font-size: 20px;
}

input {
  margin-top: 8px;
  width: 100%;
  height: 63px;
  border-radius: 5px;
  border: 2px solid hsl(240, 2%, 18%);
  padding-left: 24px;
  color: white;
  font-size: 20px;
  outline: none;
}

.password-f-g input {
  padding-right: 50px;
}

.email-f-g input {
  padding-right: 50px;
}
input::placeholder {
  color: rebeccapurple;
  font-size: 18px;
  color: #bcbcbc;
  font-weight: 400;
}
.btn {
  min-width: 100%;
  height: 65px;
  background-color: #0057ff;
  color: white;
  letter-spacing: 4px;
  font-size: 19px;
  border: none;
  border-radius: 8px;
}
.sign-in-code-button {
  background-color: #505660;
}
.sign-in-Button {
  margin-top: 20px;
}
.or-text {
  text-align: center;
  font-size: 22px;
  color: #bcbcbc;
  padding: 5px;
}
.company-services {
  text-align: center;
  color: #bcbcbc;
  margin-top: 20px;
  padding: 3px;
  background-color: #2d3137;
}
.sign-in-footer {
  width: 556px;
  position: absolute;
  bottom: 0;
}
.sign-in-footer i {
  color: #ffffff;
  font-size: 11px;
  padding-left: 3px;
}
.our-partners {
  background-color: #24272c;
  padding: 30px;
  border-bottom-left-radius: 15px;
  border-bottom-right-radius: 15px;
}
.footer-title {
  font-size: 10px;
  letter-spacing: 4px;
  text-align: center;
}
ul {
  list-style: none;
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin: 28px;
}
.other-app-title {
  text-align: center;
  color: #d5d5d5;
}
.btn:hover {
  cursor: pointer;
}

/*  ..............................Media Query Here............................ */

@media only screen and (max-width: 600px) {
  body {
    background-color: black;
  }
  .sign-in-component {
    padding-top: 7px;
    background-color: black;
    width: 100%;
    border: none;
  }

  .error {
    text-align: center;
    font-size: 13px;
  }
  .sign-in-footer {
    width: 100%;
  }
  .our-partners {
    border-bottom-left-radius: 0;
    border-bottom-right-radius: 0;
    height: auto;
  }
  .check-box-group span,
  .forgot-password-box a,
  label {
    font-size: var(--mobile-label);
  }
  .btn {
    height: 60px;
  }
  input::placeholder {
    font-size: 15px;
  }
  input {
    height: 58px;
    background-color: #1c1c1ec1;
  }
  ul li img {
    /* width: 10px; */
    justify-content: space-between;
    width: 12vw;
  }
}
@media only screen and (min-device-height: 900px) and (max-device-width: 768px) {
  .sign-in-component {
    /* background-color: firebrick; */
    height: 100vh;
  }
  .our-partners {
  }
}
</style>
