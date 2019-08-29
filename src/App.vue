<template>
    <div>
        <p>
            <section class="section">
                <div class="container">
                    <h1 class="title">App</h1>
                    <!-- <hello-world v-if="show" />
                    <button v-on:click="show = true" class="help is-success">Show</button> -->
                   <nav-bar />
                    <hr />
                    <router-view />
                </div>
            </section>
        </p>
    </div>
</template>

<script>
//=>yarn add bulma
import 'bulma/css/bulma.min.css';
import { head } from './vue-head';
import Navbar from '@/components/Navbar';

const HelloWorld = () => import('@/components/HelloWorld' /* webpackChunkName: 'hello-world' */)

export default {
    head: head,
    data(){
        return {
            show: false      
        }
    },
    components: {
        'nav-bar': Navbar,
        'hello-world': HelloWorld
    }
}
</script>

<style>
body{
    font-family: 'Taviraj', serif;
}

.router-link-active {
    color: cadetblue;
}
</style>