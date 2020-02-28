<template>
  <vc-donut
    background="white"
    foreground="#E8E8E8"
    :size="150"
    unit="px"
    :thickness="50"
    :sections="sections"
    :total="130"
    :start-angle="240"
    @section-click="handleSectionClick"
  >
    <div class="dough-dark">+5,650</div>
    <div class="dough-light">USD</div>
  </vc-donut>
</template>
<script>
export default {
  data() {
    return {
      sections: [{ label: '13%', value: 25, color: '#FD9949' }]
    };
  },
  methods: {
    handleSectionClick(section, event) {
      console.log(`${section.label} clicked.`);
    }
  }
};
</script>
<style scoped>
.dough-light {
  color: #a6a9b7;
  font-size: 10px;
  font-weight: 500;
}

.dough-active {
  font-size: 11px;
  position: absolute;
  left: 12%;
  top: 22%;
  color: white;
}
</style>
