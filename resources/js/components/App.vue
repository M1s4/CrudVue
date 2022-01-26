<template>
    <div>
      <main>
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
          <div class="container-fluid">
            <img src="https://vuejs.org/images/logo.svg" class="" width="30" height="24" alt="">
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
              <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                <li>
                    <router-link exact-active-class="active" to="/" class="nav-link active" aria-current="page">
                     Inicio
                    </router-link>
                    </li>
                     <li>
                    <router-link exact-active-class="active" to="/blogs" class="nav-link active" aria-current="page">
                     Blogs
                    </router-link>
                    </li>
                     <li>
                    <router-link exact-active-class="active" to="/contacto" class="nav-link active" aria-current="page">
                     Contacto
                    </router-link>
                    </li> 
              </ul>
              <form class="d-flex">
                <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
                <button class="btn btn-outline-success" type="submit">Search</button>
              </form>
            </div>
          </div>
        </nav>
        <div>
          <router-view></router-view>
        </div>
      </main>
        
    </div>
</template>