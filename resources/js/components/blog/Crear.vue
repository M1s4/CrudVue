<template>
    <div class="container">
        <div class="row">

          <div class="col-12">

            <div class="card">

               <div class="card-header">
                 <h4>Crear Blog</h4>
               </div>

            </div>
            <div class="card-body">
               <form @submit.prevent="crear">
                  <div class="row">
                    <div class="col-12 mb-2">
                      <div class="form-group">
                        <label>Titulo</label>
                        <input type="text" class="form-control" v-model="blog.titulo">
                      </div>
                    </div>
                    <div class="col-12 mb-2">
                      <div class="form-floating">
                        <textarea class="form-control"  v-model="blog.contenido" id="floatingTextarea2" style="height: 100px"></textarea>
                        <label for="floatingTextarea2">Contenido</label>
                      </div>
                    </div>
                    <div class="col-12">
                     <button type="submit" class="btn btn-primary"> Guardar</button>
                    </div>
                  </div>
               </form>
            </div>

          </div>

        </div>
    </div>
</template>

<script>

export default {
name: "Crear-blog",
data() {
  return {
    blog:{
      titulo:"",
      contenido:""
    }
  }
},
methods:{
  async crear (){
    await this.axios.post('/api/blog', this.blog)
     .then(response=>{
       this.$router.push({name:"mostrarBlogs"})
     })
     .catch(error=>{
       console.log(error);
     })
  }
}  
}
</script>