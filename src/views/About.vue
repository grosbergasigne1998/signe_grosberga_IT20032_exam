<script>
import { auth } from '@/stores/auth'
import songList from '@/data/songs'

export default {
    data() {        
        return{
            songs: songList,
            favoriteList:true,
            editingForm: false,
            name: auth.name,
            surname : auth.surname,
            studentCode: auth.code

    }},
    methods: {
        toggleEdit() {
                if(this.editingForm) {
                    this.editingForm = false;
                } else {
                    this.editingForm = true;
                }
            },
            btnText(){
                if (this.editingForm) {
                    return "Cancel"
                } else return "Edit form"
            },
    },
    computed:{}
}

</script>


<template>

    <div id="about-view">
        <div class="wrapper-header">
            <h1>ABOUT ME</h1>
            <div class="settings">
                <button id="btn-edit" v-bind:class="[{ active : editingForm }]" @click="toggleEdit()" v-text="btnText()"></button>
                <button id="btn-save">Save Form</button>
            </div>
        </div>
        <form>
            <div class="wrapper-input">
            <label>NAME</label>
            <input v-show="editingForm" id="input-name" :placeholder="name"/>
            <p id="txt-name" v-show="!editingForm">{{name}}</p>
        </div>
        <div class="wrapper-input">
            <label>SURNAME</label>
            <input v-show="editingForm" id="input-surname" :placeholder="surname"/>
            <p id="txt-surname" v-show="!editingForm">{{surname}}</p>
        </div>
        <div class="wrapper-input">
            <label>STUDENT CODE</label>
            <input v-show="editingForm" id="input-code" :placeholder="studentCode"/>
            <p id="txt-code" v-show="!editingForm">{{studentCode}}</p>
        </div>
            <div class="wrapper-songs">
                <label>FAVORITE SONGS</label>
                <ul>
                    <li>
                        <img id="img-album" src="https://i.scdn.co/image/ab67616d00001e02980c9d288a180838cd12ad24" />
                        <div class="song-info">
                            <p id="txt-song" class="song-name">DEEP (feat. Nonô)</p>
                            <p id="txt-artist" class="song-artists">Example</p>
                        </div>
                    </li>
                </ul>
                <div id="txt-empty" class="empty">NO SONGS FOUND</div>
            </div>
        </form>
    </div>
</template>