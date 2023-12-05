<template>
    <div class="about">
    
        <nav class="navbar navbar-expand-sm bg-cyan-950 text-white col-xl-12 col-md-12 col-sm-12 ">
          <div class="container-fluid">
            <button
              class="navbar-toggler text-white bg-white"
              type="button"
              data-bs-toggle="collapse"
              data-bs-target="#navbarTogglerDemo03"
              aria-controls="navbarTogglerDemo03"
              aria-expanded="false"
              aria-label="Toggle navigation"
            >
              <span class="navbar-toggler-icon"></span>
            </button>
            <div class="flex">      
                 <img class="w-20 h-20 ms-5" src="src/assets/grow.png" alt="compant name"/>
                 <h3 class="text-slate-200 mt-10 ms-1">Growth <br/> school</h3>
            </div>
   
            <div class="collapse navbar-collapse" id="navbarTogglerDemo03">
              <ul class="navbar-nav ms-auto">
                <!-- <button class="c-name btn btn-sucess"> Srikanth O- farms(logo)</button>  -->
                <li class="nav-item">
                  <!-- <a class="nav-link text-white" href="#">Home</a> -->
                  <router-link class="nav-link text-white" to="/" exact>home</router-link>
                </li>
                <li class="nav-item">
                  <a class="nav-link text-white" href="#"> Contact</a>
                  <router-link class="nav-link text-white" to="/about">about</router-link>
                </li>
                <li class="nav-item">
                  <!-- <a class="nav-link text-white" href="#"> Contact</a> -->
                  <router-link class="nav-link text-white" to="/contact">contact</router-link>
                </li>
                <li class="nav-item">
                  <!-- <a class="nav-link text-white" href="#">Products</a> -->
                  <router-link class="nav-link text-white" to="/products">products</router-link>
                </li>
                <li>
                  <div class="dropdown">
                    <button
                      type="button"
                      class="btn btn-success dropdown-toggle"
                      data-bs-toggle="dropdown"
                    >
                      Dropdown button
                    </button>
                    <ul class="dropdown-menu">
                      <li><a class="dropdown-item" href="/contact">Normal</a></li>
                      <li><a class="dropdown-item active" href="#">Active</a></li>
                      <li><a class="dropdown-item disabled" href="#">Disabled</a></li>
                    </ul>
                  </div>
                </li>
                <li>
                  <div class="dropdown">
                    <button
                      type="button"
                      class="btn btn-success dropdown-toggle"
                      data-bs-toggle="dropdown"
                    >
                      Why Chicken
                    </button>
                    <ul class="dropdown-menu">
                      <li><a class="dropdown-item" href="#">Normal</a></li>
                      <li><a class="dropdown-item active" href="#">Active</a></li>
                      <li><a class="dropdown-item disabled" href="#">Disabled</a></li>
                    </ul>
                  </div>
                </li>
              </ul>
            </div>
          </div>
        </nav>
      
      <router-view></router-view>
    </div>
   
  </template>
  
  
  <style>
  
  .logo-image {
    width: 109px;
    height: 85px;
    border-radius: 12px;
  }
 
 
 
 
  
  
  
  </style>
  