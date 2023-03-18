<template>
  <div>
    <h2 class="page">Looking for something?</h2>
    <h4 class="page">We can't find this page.</h4>
    <img
      src="https://demo.activeitzone.com/ecommerce/public/assets/img/404.svg"
      class="pic"
    />
    <div class="link"><router-link class="routes" to="/home">Go Back To Home</router-link>.</div>
    
  </div>
</template>

<script>
export default {};
</script>

<style>
.page {
  display: flex;
  align-items: center;
  text-align: center;
  justify-content: center;
  
}
.align {
  text-align: center;
}

.pic {
  height: 60rem;
  width: 50rem;
  margin-left: 35%;
}
.routes {
  background-color: var(--dim-blue);
  color: #fff;
  padding: 2rem;
  font-size: medium;
}
.link {
  display: flex; 
  align-items: center;
  justify-content: center;
}
</style>
