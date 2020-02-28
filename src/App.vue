<template>
  <div id="app">
    <div id="nav">
      <Navigation @check="value = $event" />
    </div>
    <div id="route">
      <router-view />
    </div>
  </div>
</template>

<script>
import Navigation from './components/Navigation';
export default {
  data() {
    return {
      value: ''
    };
  },
  components: {
    Navigation
  },
  watch: {
    value(x) {
      let body = document.querySelectorAll('body')[0];
      let nav = document.getElementById('nav');
      let exact = document.getElementsByClassName('router-link-exact-active');
      if (x == true) {
        body.style.background = '#262B56';
        body.style.color = '#ffffff';
        nav.style.background = '#262B56';
        $('a.router-link-exact-active svg').css('background', 'white');
        $('a.router-link-exact-active svg path').css('fill', '#43424b');
        $('.dough-dark').css('color', '#43424B');
      } else {
        body.style.background = '#ffffff';
        body.style.color = '#43424B';
        nav.style.background = '#ffffff';
        $('a.router-link-exact-active svg').css('background', '#43424b');
        $('a.router-link-exact-active svg path').css('fill', '#ffffff');
        $('.dough-dark').css('color', '#43424B');
      }
    }
  }
};
</script>
<style>
body {
  box-sizing: border-box;
  margin: 0;
  background: #ffffff;
  transition: 0.5s background ease;
}
#app {
  font-family: 'Muli', 'Poppins';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#nav {
  width: 18vw;
  position: fixed;
  left: 0;
  top: 0;
  height: 100vh;
  padding: 1.5rem 1.5rem 0.7rem;
  background: white;
  transition: 0.5s background ease;
}

#route {
  margin-left: 18vw;
  flex: 1;
  border-left: 1px solid #e8e8e8;
  min-height: 100vh;
  padding-left: 1rem;
  padding-top: 1.5rem;
}

#nav a {
  color: #a6a9b7;
  font-family: 'Poppins';
  font-size: 12px;
  font-weight: 500;
  text-decoration: none;
}
#nav a svg {
  height: 21px;
  width: 21px;
  padding: 5px;
  margin-right: 5px;
  border-radius: 4px;
  margin-bottom: 1px;
}
#nav a.router-link-exact-active {
  color: #43424b;
  font-family: 'Poppins';
}
#nav a.router-link-exact-active svg {
  background: #43424b;
  padding: 5px;
  height: 21px;
  width: 21px;
  color: #ffffff;
}
#nav a.router-link-exact-active svg path {
  fill: #ffffff;
}
.link-bottom-text {
  font-size: 12px;
  font-weight: 700;
  color: #43424b;
}
</style>
