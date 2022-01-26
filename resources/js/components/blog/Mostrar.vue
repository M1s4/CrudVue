<template>
  <div class="container">
    <div class="row">
        <div class="col-12 mb-12">
           <router-link :to='{name:"crearBlog"}' class="btn btn-success position-absolute top-50 start-50 translate-middle ">
            Agregar dato <i class="fas fa-plus "></i>
           </router-link>
        </div>

        <div class="col-12">
           <div class="tab  le-responsive">
             <table class="table table-bordered">
                <thead class="bg-primary text-white">
                  <tr>
                    <th>ID</th>
                    <th>DATO UNO</th>
                    <th>DATO DOS</th>
                    <th>ACCIONES </th>
                  </tr>
                </thead>
                <tbody>
                   <tr v-for="blog in blogs" :key="blog.id">
                    <td>{{blog.id}}</td>
                    <td>{{blog.titulo}}</td>
                    <td>{{blog.contenido}}</td>
                    <td>
                      <router-link :to='{name:"editarBlog", params:{id:blog.id}}' class="btn btn-info">
                        <i class="fas fa-edit"></i>
                      </router-link>
                      <a type="button" @click="borrarBlog(blog.id)" class="btn btn-danger">
                        <i class="fas fa-trash"></i>
                      </a>
                    </td>                    
                   </tr>
                </tbody>
             </table>
           </div>
        </div>
    </div>
  </div>
</template>
 <script>
 export default {
   name:"blogs",
   data(){
     return{
       blogs:[]
     }
   },
   mounted() {
     this.mostrarBlogs()
   },
   methods: {
     async mostrarBlogs(){

       await this.axios.get('/api/blog')
        .then(response=>{
          this.blogs = response.data
        })
        .catch(error=>{
          this.blog = []
        })
     },

     borrarBlog(id){
       if(confirm("?confirma la eliminacion del registro?")){
         this.axios.delete(`/api/blog/${id}`)
         .then(response=>{
          this.mostrarBlogs()
        })
        .catch(error=>{
          console.log(error);
        })
       }

     }

   },
 }
 </script>