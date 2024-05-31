<template>
  <div class="logo-container">
    <div class="logo-img-box">
      <img
        class="logo-icon"
        src="../../public/company-logo.svg"
        alt="MGM Global Distribution Logo"
      />
      <h4 class="logo-title">Global<br />Distribution</h4>
    </div>
  </div>
</template>

<style scoped>
.logo-container {
  background-color: transparent;
  /* background-color: red; */
  height: 74px;
  color: white;
  margin: 13px auto 0 auto;
  display: flex;
  justify-content: center;
}
.logo-icon {
  /* padding-top: 10px; */
  display: flex;
  /* align-items: center; */
  /* justify-content: center; */
}
.logo-img-box {
  display: flex;
  gap: 6px;
}
.logo-title {
  font-size: 20px;
  font-weight: 600;
}

@media only screen and (max-width: 600px) {
  .logo-container {
    /* height: 100px; */
    margin-top: 0;
    justify-content: left;
  }
}
</style>
