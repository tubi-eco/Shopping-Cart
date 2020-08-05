<template>
  <div class="container">
    <shopping-header></shopping-header>
    <div class="row book-list" v-for="book in books" :key="book.id">
      <div class="col-6 justify-content-start">
        <div class="d-flex justify-content-start">
          <div class="book-cover">
            <img v-bind:src="book.thumbnail"/>
          </div>
          <div class="book-details">
            <div class="book-title">{{book.name}}</div>
            <div class="author">{{book.author}}</div>
          </div>
        </div>
      </div>
      <div class="col-6 buy-details">
        <ul class="row">
          <li class="col-sm">{{ book.format }}</li>
          <li class="col-sm">
            <div class="d-flex justify-content-end">
              <button class="btn-counter" @click="counterDecrease(book.id)">-</button>
              <div class="counter">{{book.counter}}</div>
              <button class="btn-counter" @click="counterIncrease(book.id)">+</button>
            </div>
          </li>
          <li class="col-sm price">
            <span v-if="showPrice">{{ book.price }}</span>
            <span v-else>{{ book.price*book.counter }}</span>
          </li>
        </ul>
      </div>
      <hr/>
    </div>

    <div class="total-container">
      <div>
        <span>Sub Total</span>:<br>
        <span>Shipping</span>:<br>
        <span>Total(Tax included)</span>:
      </div>
      <div>
         ${{ formatPrice(total()) }}<br>
         $2.99<br>
         ${{ formatPrice(total() + 2.99)  }}
      </div>
      </div>
      <div  class="row d-flex justify-content-end">
        <button class="checkout-btn">Checkout <span>${{ formatPrice(total() + 2.99)  }}</span></button>
      </div>
  </div>
</template>

<script>
    import ShoppingHeader from "./ShoppingHeader";
    import axios from "axios";
    const button = document.getElementsByClassName('btn-danger');

    export default {
      data(){
        return {
          showPrice : true,
        }
      },
      components : {
        ShoppingHeader
      },
      created(){
        var bookList = []
        this.$store.state.books =  []
        axios.get("./products.json").then(response => {
            let data = response.data;
            for(let key in data){
              bookList.push({ ...data[key], id : key, counter: 1 })
            }
            this.$store.state.books = bookList
          })
          .catch(e => console.log("error"))
      },
      computed :{
        books (){
          return this.$store.getters.books;
        }
      },
      methods : {
        formatPrice(value) {
          let val = (value/1).toFixed(2).replace('.', ',')
          return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".")
        },
        counterIncrease (bookId){
           this.$store.state.counter++;
           this.books.find(b => b.id == bookId).counter++;
           this.showPrice = false;
           this.total();
        },
        counterDecrease (bookId){
           this.showPrice = false;
           if(this.books.find(b => b.id == bookId).counter > 0){
             this.books.find(b => b.id == bookId).counter--;
           }
           this.total();
        },
        total() {
          return this.books.reduce(function (sum, book) {
            return sum + (book.price * book.counter)
          }, 0)
        }
      }
    }
</script>

<style scoped lang="scss">
  ul{
    padding: 0;
    margin:0;
    li{
      list-style: none;
      text-align: right;
    }
  }
  .book-list{
    padding: 20px 0;
    background: #e5e9ea;
    border-bottom: 1px solid #fff;
    &:nth-last-child(2){
      border-bottom: 2px dashed #fff!important;
    }
    .book-cover{
      img{
        max-height: 110px;
      }
    }
    .book-details{
      margin-left: 15px;
      .book-title{
        font-size: 14px;
        font-weight: 700;
      }
      .author{
        font-size: 13px;
      }
    }
    .price{
      font-weight: 400;
    }
  }
  .buy-details{
    font-size: 14px;
    font-weight: 300;
    ul{
      li{
        &:nth-last-child(1),
        &:nth-child(1){
          margin-right: 5px;;
        }
        @media (max-width: 767px) {
          margin-bottom: 15px;
        }
      }
    }
  }
  .btn-counter{
    color: #666;
    width: 15px;
    height: 15px;
    display: block;
    margin-bottom: 5px;
    border-radius: 2px;
    text-align: center;
    padding: 0;
    margin: 4px 0 2px;
    line-height: 0;
    font-size: 16px;
    border: 0;
    background: transparent;
    &:focus,
    &:visited{
      outline:0px;
    }
    &:nth-child(1){
      margin-right: 5px;
    }
    &:nth-last-child(1){
      margin-left: 5px;
    }
  }
  .counter{
    font-size: 12px;
    font-weight: 400;
    background: #fff;
    width: 20px;
    height: 20px;
    text-align: center;
  }
  .total-container{
    background: #e5e9ea;
    padding: 15px 15px 35px;
    text-align:right;
    margin: 0 -15px;
    font-size: 16px;
    font-weight: 700;
    span{
      font-size: 14px;
      color: #666;
      display: inline-block;
      width: 150px;
      margin-right: 10px;
    }
    div{
      display: inline-block;
    }
  }
  .checkout-btn{
    background: #f2c40e;
    padding: 10px 15px;
    border-radius: 6px;
    color: #fff;
    font-size: 18px;
    text-align: left;
    border: 0;
    min-width: 220px;
    margin-top: -20px;
    span{
      display: inline-block;
      float: right;
    }
  }
</style>
