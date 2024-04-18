<template>
    <div>
      <ul class="nav">
        <li>
          <router-link tag="li" to="/" exact>Home</router-link>
        </li>
        <li>
          <router-link tag="li" to="/categories">Categories</router-link>
        </li>
        <li>
          <router-link tag="li" to="/about">About</router-link>
        </li>
      
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: "Mainmenu"
  };
  </script>
  
  <style lang="scss" scoped>
  .nav{
    overflow: hidden;
    display: flex;
    justify-content: center;
    margin-bottom: 50px;
    li{
      display: inline-block;
      padding: 10px;
      margin: 0 5px;
      a{
        text-decoration: none;
        color: #4f4f60;
        font-weight: bold;
      }
    }
    li:hover{
      border-bottom: 3px solid #4c4f60;
  
  
    }
  }
  </style>