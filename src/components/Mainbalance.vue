<template>
  <main class="main-balance">
    <div class="mb-title">Current Balance</div>
    <div class="mb-figure d-flex m-0 p-0 align-items-center">
      <div>
        <span class="dollar" style="font-size:16px; bottom:2px">$</span
        >16,756.00
      </div>
    </div>
  </main>
</template>

<script>
export default {};
</script>

<style scoped>
.main-balance {
  height: 5.6rem;
  width: 100%;
  border-radius: 6px;
  border: none;
  background: linear-gradient(87.79deg, #fe6dad -17.06%, #fc9f35 131.64%);
  box-shadow: -9px 20px 40px rgba(254, 109, 173, 0.28);
  color: white;
  line-height: 24px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 0 1.5rem;
  position: relative;
}
.main-balance::before {
  position: absolute;
  width: 80%;
  height: 6rem;
  content: '';
  top: -1px;
  margin: auto;
  z-index: -1;
  background: transparent linear-gradient(89deg, #fe6dad 0%, #fc9f35 100%) 0% 0%
    no-repeat padding-box;
  border-radius: 8px;
  opacity: 0.47;
  filter: blur(21px);
}
.mb-title {
  font-size: 12px;
  font-weight: bold;
  opacity: 0.9;
}
.mb-figure {
  font-size: 26px;
  font-weight: bold;
  opacity: 0.9;
}
.dollar {
  position: relative;
  bottom: 1px;
}
</style>
