<template>
  <div class="row shopping-header">
    <div class="col-sm">
      <h2>
        Shopping Header
      </h2>
    </div>
    <div class="col-sm mobile-hide">
      <ul class="row">
        <li class="col-sm">Format</li>
        <li class="col-sm">Quantity</li>
        <li class="col-sm">Price</li>
      </ul>
    </div>
  </div>
</template>

<script>
    export default {
        name: "ShoppingHeader"
    }
</script>

<style scoped lang="scss">
.shopping-header{
    background: #ecf0f1;
    padding: 15px 5px;
    border-top-left-radius: 5px;
    border-top-right-radius: 5px;
    h2{
      line-height: 20px;
     @media (max-width:767px)
      {
        line-height: inherit;
      }
    }
    ul{
    padding: 0;
    margin:0;
    li{
      list-style: none;
      text-align: right;
    }
  }
}
</style>
