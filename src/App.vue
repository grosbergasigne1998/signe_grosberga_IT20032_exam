<script>
import { computed } from '@vue/reactivity';
import { auth } from '@/stores/auth.js'
export default {
data() {
    return {
       authoriside: auth.is_authoriside
    }
},
}
</script>

<template>
    <Header  v-if="authoriside">   
    </Header>
<div id="section-body">
        <Nav  v-if="authoriside">
        </Nav>
        <router-view class="section-router"></router-view>
</div>
    <div  v-if="authoriside" id="section-player">
        <AudioPlayer />
    </div>
</template>

