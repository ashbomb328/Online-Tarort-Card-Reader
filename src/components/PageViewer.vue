<template>
<div class="container">
        <h1 class="emphasize login-box"> {{page.pageTitle}} </h1>
        <!-- <p1 class="emphasize">{{page.content}} </p1> -->

    </div>
</template>

<script>
export default{
    props: {
        page : {
            type: Object,
            default(rawProps) {
                return {
                    pageTitle: '',
                    content: ''
                };
            }
        }
    }
}
</script>

<style scoped>
.emphasize {
    color: #874794;
    text-align: center;
    margin-top: 20px;
}
/* Add a card effect for divs */
.card {
        background-color: rgb(255, 255, 255);
        padding: 10px;
        text-align: center;
        margin-top: 240px;
    }
    .login-box {
      font-family: 'Roboto', sans-serif;
      margin-top: 2%;
      margin-bottom: auto;
      height: auto;
      width: auto;
      background: #1A2226;
      text-align: center;
      border-radius: 10px;
      box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16), 0 3px 6px rgba(0, 0, 0, 0.23);
  }
  
  .login-title {
      text-align: center;
      font-size: 30px;
      letter-spacing: 2px;
      font-weight: bold;
      color: #874794;
  }  

</style>