<script>
import { auth } from '@/stores/auth.js'
export default {
    data() {
        return {
            email: '',
            password: '',
            auth
        }
    },
    computed: {
        isDisabled() {
            return this.email.length < 4 || this.password.length < 6;
        }
    }
}``
</script>

<template>
    <div id="login-view">
        <form class="login-form">
            <div class="wrapper-logo">
                <img src="@/assets/logo.svg" />
                <div>KRAKEN.FM</div>
            </div>
            <input v-model="email" id="input-email" placeholder="E-mail" />
            <input v-model="password" id="input-password" type="password" placeholder="Password" />
            <button id="btn-submit" :disabled="isDisabled" @click="auth.authenticate(email, password)">LOGIN</button>
        </form>
    </div>
</template>