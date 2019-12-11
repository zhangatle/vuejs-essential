<template>
  <div class="navbar navbar-default topnav">
    <div class="container">
      <div class="navbar-header">
        <button class="navbar-toggle" type="button" @click="toggleNav">
          <span class="sr-only">Toggle navigation</span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </button>
        <router-link to="/" class="navbar-brand">
          <span class="title">{{logo.title}}</span>
          <img :src="logo.src" :alt="logo.title">
        </router-link>
      </div>
      <div id="top-navbar-collapse" :class="['collapse','navbar-collapse',{in:showCollapseNav}]">
        <ul class="nav navbar-nav">
          <li v-for="(item,index) in navList" :class="{active: index === activeNavIndex}">
            <a href="#" @click="changeNavIndex(index)">{{item}}</a>
          </li>
        </ul>
        <div class="navbar-right">
          <TheEntry/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    import TheEntry from "@/components/layouts/TheEntry"
    export default {
        name: "TheHeader",
      components: {TheEntry},
      comments: 'TheEntry',
        data(){
          return {
            logo: {
              src: `${this.uploadsUrl}6Ox1bjeh1BF3odCf/it/u=3533778697,2586993014&fm=74&app=80&f=PNG&size=f121,121?sec=1880279984&t=1dbed90be2871a78074bf731b6872ed0`,
              title: 'VuejsCaff'
            },
            activeNavIndex: 0,
            navList: ['社区','头条','问答','教程'],
            showCollapseNav: false
          }
        },
      beforeCreate() {
          this.uploadsUrl = 'https://dss0.bdstatic.com/'
      },
      methods: {
          changeNavIndex(index){
            this.activeNavIndex = index
          },
          toggleNav(){
            this.showCollapseNav = !this.showCollapseNav
          }
      }
    }
</script>

<style scoped>
.title {display: none}
  .navbar-default .navbar-nav > .active >a {background: rgba(0,0,0,0.03);}
</style>
