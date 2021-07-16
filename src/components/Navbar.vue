<template>
    <header class="header header-cstm">
        <div class="container">
            <div class="header-inner">
                <div class="header-left">
                    <div class="head-logo">
                        <a href="#"><img src="../assets/images/logo.png"></a>
                    </div>
                    <div class="navbar-cstm">
                        <ul class="ul-bar">
                            <li><a href="#">Dashboard</a></li>
                            <li><a href="#">Messages</a></li>
                            <li class="active"><a href="#">Order</a></li>
                            <li><a href="#">Gigs</a></li>
                            <li><a href="#">Analtics</a></li>
                            <li><a href="#">Earnings</a></li>
                        </ul>
                    </div>
                </div>
                <div class="header-right">
                    <div class="profile-pic">
                        <a href="#"><img src="../assets/images/ppl-1.jpg" /></a>
                        <span class="span-online"></span>
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>
<script lang="ts">
    import { Component, Vue } from 'vue-property-decorator';

    @Component({
        components: {
        },
    })
    export default class Navbar extends Vue {}
</script>