<script setup>
import { ref, reactive, watch } from 'vue'
import { onMounted, onUpdated } from 'vue'
import * as EmailValidator from 'email-validator'
import * as PhoneValidator from 'validate-phone-number-node-js'
const usernameRef = ref(null)
const username = ref('')
const password = ref('')
const password2 = ref('')
const disabled = ref(true)
const validUsername = ref(false)
const validPassword = ref(false)
const validEmail = ref(false)
const validPhone = ref(false)
const passwordsMatch = ref(false)
const usernameErrorRef = ref(null)
const passwordErrorRef = ref(null)
const password2ErrorRef = ref(null)
const email = ref('')
const emailErrorRef = ref(null)
const phone = ref('')
const phoneErrorRef = ref(null)
const user = reactive({
    avatarImageFile: {}
});
// watch element ref - similar to onMounted - not watching value of input
// for some reason disabled when ref function is installed 
function loadPreviewImg(evt) {
    user.avatarImageFile = evt.target.files[0]
    let reader = new FileReader()
    reader.onloadend = function () {
        let img = document.querySelector("#preview-img")
        img.src = reader.result;
    }
    reader.readAsDataURL(user.avatarImageFile)
}

let count = 0
watch(usernameRef, () => {
    console.log('watching usernameRef')
    console.log(usernameRef.value)
    console.log(count++)
    usernameRef.value.value = ""
})
// called when anything in component changes - including onMounted
//watch v-model input.value ref (called when string changes)
watch(username, () => {
    validUsername.value = (username.value.length >= 4)
    usernameErrorRef.value.innerHTML = (validUsername.value) ?
        "&nbsp;" : "Minimum length: 4 characters"
    usernameRef.value.setAttribute("data", "hello")
})
// watch array of refs
watch([password, password2], () => {
    passwordsMatch.value = (password.value === password2.value)
    password2ErrorRef.value.innerHTML = (passwordsMatch.value || password2.value.length == 0) ?
        "&nbsp;" : "Passwords do not match"
})
//watch password field and validate
watch(password, () => {
    console.log("password changed")

    if (passwordErrorRef.value != null && password.value.length > 0) {
        validPassword.value = (password.value.length >= 8)
        passwordErrorRef.value.innerHTML = (validPassword.value) ?
            "&nbsp;" : "Minimum length: 8 characters"
    }

    if (passwordErrorRef.value != null && password.value.length > 0) {
        validPassword.value = /[!@#$%^&*]/.test(password.value);
        passwordErrorRef.value.innerHTML = (validPassword.value) ?
            passwordErrorRef.value.innerHTML + "&nbsp;" : "Must include a special character"
    }

    if (passwordErrorRef.value != null && password.value.length > 0) {
        validPassword.value = /[A-Z]/.test(password.value)
        passwordErrorRef.value.innerHTML = (validPassword.value) ?
            passwordErrorRef.value.innerHTML + "&nbsp;" : "Must include an uppercase character"
    }

    if (passwordErrorRef.value != null && password.value.length > 0) {
        validPassword.value = /[a-z]/.test(password.value)
        passwordErrorRef.value.innerHTML = (validPassword.value) ?
            passwordErrorRef.value.innerHTML + "&nbsp;" : "Must include a lowercase character"
    }
}) 
// watch array of refs
watch([validUsername, validPassword, passwordsMatch, validEmail, validPhone], async () => {
    disabled.value = !(validUsername.value && validPassword.value && passwordsMatch.value && validEmail && validPhone)
    console.log(disabled.value)
    if (!disabled.value) usernameRef.value.value = ''
})
watch(email, () => {
    validEmail.value = (EmailValidator.validate(email.value))
    emailErrorRef.value.innerHTML = (validEmail.value) ?
        "&nbsp;" : "Invalid email format"
})
watch(phone, () => {
    validPhone.value = (PhoneValidator.validate(phone.value))
    phoneErrorRef.value.innerHTML = (validPhone.value) ?
        "&nbsp;" : "Invalid phone number format"
})
function submit() {
    let mssg = username.value + ", " + password.value
    console.log(mssg)
}
onMounted(() => {
    usernameRef.value.focus();
})
onUpdated(() => {
    //console.log(usernameRef.value.value)
})
</script>


<template>
    <div class="container" id="mainDiv">
        <form class="rounded border border-primary border-2 border-opacity-25 py-3 px-5">
            <fieldset class="d-flex flex-column">
                <legend>Create Account</legend>

                <div class="form-floating mb-2">
                    <label for="username" class="form-label">Username</label><br>
                    <input ref="usernameRef" v-model="username" id="username" type="text" class="form-control" /><br>
                    <small ref="usernameErrorRef" class="text-danger">&nbsp</small>
                </div>

                <div class="form-floating mb-2">
                    <label for="password" class="form-label">Password</label><br>
                    <input v-model="password" id="password" type="password" class="form-control" /><br>
                    <small ref="passwordErrorRef" class="text-danger">&nbsp;</small>
                </div>

                <div class="form-floating mb-2">
                    <label for="password2" class="form-label">Reenter password</label><br>
                    <input v-model="password2" id="password2" type="password" class="form-control" /><br>
                    <small ref="password2ErrorRef" class="text-danger">&nbsp;</small>
                </div>

                <div class="form-floating mb-2">
                    <label for="email" class="form-label">Email</label><br>
                    <input v-model="email" id="email" type="text" class="form-control"
                        placeholder="example@gmail.com" /><br>
                    <small ref="emailErrorRef" class="text-danger">&nbsp;</small>
                </div>

                <div class="form-floating mb-2">
                    <label for="phone" class="form-label">Phone Number</label><br>
                    <input v-model="phone" id="phone" placeholder="+17575553333" type="text" class="form-control" /><br>
                    <small ref="phoneErrorRef" class="text-danger">&nbsp;</small>
                </div>

                <div>
                    <button @click="submit" class="btn btn-primary" type="button"
                        v-bind:disabled="disabled">Create</button>
                </div>
                <div>
                    <label for="avatar" class="form-label">Choose a profile picture:</label>

                    <input id="avatar" class="form-control" type="file" name="avatar" accept="image/png, image/jpeg"
                        @change="loadPreviewImg">
                </div>
                <div>
                    <img id="preview-img"> {{ user.avatarImageFile.name }}
                </div>
            </fieldset>
        </form>
    </div>

</template>

<style>
label {
    margin-top: 15px;
}

small {
    color: red;
}

button {
    margin-top: 10px;
    padding-top: 7px;
    padding-bottom: 7px;
    padding-left: 15px;
    padding-right: 15px;
}

img {
    margin-top: 20px;
    width: 200px;
    height: 200px;
}

#mainDiv {
    margin-top: 50px;
    margin-bottom: 50px;
}
</style>