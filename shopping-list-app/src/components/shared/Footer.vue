<template>
  <div class="footer">
      <!-- Site footer -->
    <div class="site-footer">
        <div class="container">
          <div class="row">
            <div class="col-sm">
              <p class="copyright-text">Copyright &copy; 2017 All Rights Reserved by 
          <a href="#">Efectura</a>.
              </p>
            </div>

            <div class="col-sm text-right">
              <ul class="social-icons">
                <li><a class="facebook" href="#"><i class="fa fa-facebook"></i></a></li>
                <li><a class="twitter" href="#"><i class="fa fa-twitter"></i></a></li>
                <li><a class="dribbble" href="#"><i class="fa fa-dribbble"></i></a></li>
                <li><a class="linkedin" href="#"><i class="fa fa-linkedin"></i></a></li>   
              </ul>
            </div>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
  export default {
    name: "Footer"
  }
</script>

<style scoped lang="scss">
  .footer {
    width: 100%;
    height: 50px;
    line-height: 50px;
    background-color: #f5f5f5;
  }



.site-footer
{
  background-color:#26272b;
  padding:15px 0;
  font-size:15px;
  line-height:24px;
  color:#737373;
  hr
  {
    border-top-color:#bbb;
    opacity:0.5;
  }
  .social-icons
  {
    text-align:right
    a
    {
      width:40px;
      height:40px;
      line-height:40px;
      margin-left:6px;
      margin-right:0;
      border-radius:100%;
      background-color:#33353d
    }
  }
  .copyright-text
  {
    margin:13px 0;
    a{
        color: #ccc;
    }
  }
}

@media (max-width:767px)
{
  .site-footer
  {
    padding-bottom:0;
    .copyright-text
    .social-icons
    {
      text-align:center
    }
    .text-right{
      text-align: center!important;
    }
  }
  
}
.social-icons
{
  padding-left:0;
  margin:10px -20px 0 0;
  list-style:none;
  li
  {
    display:inline-block;
    margin-bottom:4px;
    &.title
    {
      margin-right:15px;
      text-transform:uppercase;
      color:#96a2b2;
      font-weight:700;
      font-size:13px;
      @media (max-width:767px)
      {
          display:block;
          margin-right:0;
          font-weight:600
      }
    }
  }
  a{
    background-color:#eceeef;
    color:#818a91;
    font-size:16px;
    display:inline-block;
    line-height:35px;
    width:35px;
    height:35px;
    text-align:center;
    margin-right:8px;
    border-radius:100%;
    -webkit-transition:all .2s linear;
    -o-transition:all .2s linear;
    transition:all .2s linear;
    &:active,
    &:focus,
    &:hover
    {
      color:#fff;
      background-color:#29aafe
    }
    &.facebook:hover
    {
      background-color:#3b5998
    }
    &.twitter:hover
    {
      background-color:#00aced
    }
    &.linkedin:hover
    {
      background-color:#007bb6
    }
    &.dribbble:hover
    {
      background-color:#ea4c89
    }
  }
  &.size-sm{
    a{
      line-height:34px;
      height:34px;
      width:34px;
      font-size:14px
    }
  }
}
</style>
