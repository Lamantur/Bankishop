<template>
  <div id="app">

    <TopMenu @sendvalue=showinconsolename />
    <T-main-wrapper :msge="text" />
  </div>
</template>

<script>
import TopMenu from './components/TopMenu'
import TMainWrapper from './components/T-main-wrapper';

export default {
  data() {
    return {
      title: 'Картины эпохи Возрождения',
      text: ''

    }
  },
  methods: {
    showinconsolename(data) {
      this.text = data;
    }
  },
  name: 'App',
  components: {
    TopMenu,
    TMainWrapper
  }
}

</script>
