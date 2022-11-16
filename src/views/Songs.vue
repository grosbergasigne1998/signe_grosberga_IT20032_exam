<script>
import IconCaretUp from '@/components/icons/IconCaretUp.vue'
import IconHeart from '@/components/icons/IconHeart.vue'
import IconPlay from '@/components/icons/IconPlay.vue'
import songList from '@/data/songs.js'

import { auth } from '@/stores/auth.js'
import { player } from '@/stores/player.js'

export default {
    components: { IconHeart, IconPlay, },
     data() {
        return{
        search:'',  
        songs: songList,
        showFavorites: false,
        }
},
    computed: {
        filtered_songs() {
        let tests = this.songs;
        let temp = [];
        
        temp = tests.filter((song) => {
            return song.name.toLowerCase().includes(this.search.toLowerCase())
        });
        return temp;
        },
  },
    methods: {
        selectSong(song) {  
            player.setNowPlaying(song);
        },
        handleScroll(event) {
            this.$refs.header.classList.value = event.target.scrollTop > 100 ? 'scrolled' : '';
        },
        getArtists(artists) {
            var list = '';
            artists.forEach(element => {
                list = list.concat(element.name).concat(", ")
            })
            list = list.slice(0, -2)
            return list;
        },
}
}




</script>
<template>
    <div id="songs-view" @scroll="handleScroll">
    <div class="wrapper-header">
        <h1>SONGS</h1>
        <div class="wrapper-search">
            <input id="input-search" type="search" placeholder="Search by title..." />
        </div>
        <div class="wrapper-settings">
            <button id="btn-show-favorites" @click="showFavorites ? showFavorites = true : showFavorites = false" v-bind:class="{
          active: showFavorites}">Show Favorites</button>
        </div>
    </div>
    <div class="wrapper-songs">
        <table cellspacing="0" cellpadding="0">
            <tr ref="header">
                <th id="th-id" >#</th>
                <th id="th-title">
                    Title
                    <IconCaretUp />
                </th>
                <th id="th-artist">Artist</th>
                <th id="th-album">Album</th>
                <th id="th-duration">
                    Duration
                    <IconCaretUp />
                </th>
            </tr>
            <!-- Loop goes on this <tr> element -->
            <tr class="song" v-for="(song, index) in filtered_songs" @dblclick="selectSong(song)" v-bind:class="{active: song.id ==selectSong(song)}">
                <td id="td-index">
                    <IconPlay />
                    <span id="txt-index">1</span>
                </td>
                <td id="td-title">
                    <img src="https://i.scdn.co/image/ab67616d00001e02980c9d288a180838cd12ad24" />
                    DEEP (feat. Nonô)
                </td>
                <td id="td-artist">{{ getArtists(song.artists) }}</td>
                <td id="td-album">We May Grow Old But We Never Grow Up</td>
                <td id="td-duration">
                    3:07
                    <IconHeart @click="auth.toggleFavorite(song.id)" v-bind:class="{active: auth.getFavoriteSongs().includes(song.id)}" />
                </td>
            </tr>
        </table>
    </div>
</div>
</template>