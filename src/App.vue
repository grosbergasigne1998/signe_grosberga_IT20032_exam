<template>
    <Header></Header>
    <div id="section-body">
        <nav id="nav-main" class="wrapper-navigation">
            <ol>
                <li>
                    <a href="/">SONGS</a>
                </li>
                <li>
                    <a href="/albums">ALBUMS</a>
                </li>
                <li>
                    <a href="/about">ABOUT</a>
                </li>
            </ol>
        </nav>
        <router-view class="section-router"></router-view>
    </div>
    <div id="section-player">
        <AudioPlayer />
    </div>
</template>
