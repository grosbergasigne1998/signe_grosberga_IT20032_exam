<script>
import { auth } from '@/stores/auth.js'
export default {
    data() {
        return {
            auth
        }
    },
    computed: {
        fullName() {
            return auth.user.name + " " + auth.user.surname;
        }
    }
}
</script>

<template>
    <div id="main-header" class="active">
        <div class="wrapper-logo">
            <img src="@/assets/logo.svg" />
            <h2>KRAKEN.FM</h2>
        </div>
        <div class="wrapper-profile">
            <div class="section-user">
                <span class="avatar"></span>
                <h3 id="txt-full-name">{{ fullName }}</h3>
            </div>
            <button id="btn-logout" @click="auth.logout()">LOGOUT</button>
        </div>
    </div>
</template>
