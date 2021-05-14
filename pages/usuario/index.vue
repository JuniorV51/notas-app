<template>
    	
<div class="container-fluid">
    <div class="row">
      <div class="col-md-7 d-flex vh-100 justify-content-center">
        <div class="col-md-5  align-self-center">
          <h1 class="text-center mb-5">Cadastro Novo Usuario</h1>
          <p class="text-center">Informe os dados abaixo para se cadastrar</p>
 
          <b-form @submit.prevent="Cadastro">
            <b-form-group>
              <b-form-input
                v-model="nome"
                type="nome"
                placeholder="Nome"
                required
              ></b-form-input>
            </b-form-group>

            <b-form-group>
              <b-form-input
                v-model="email"
                type="email"
                placeholder="E-mail"
                required
              ></b-form-input>
            </b-form-group>
 
            <b-form-group>
              <b-form-input
                v-model="senha"
                type="password"
                placeholder="Senha"
                required
              ></b-form-input>
            </b-form-group>
 
            <b-button block type="submit" variant="primary">Cadastrar</b-button>
          </b-form>
        </div>
      </div>
      <div class="col-md-5 vh-100 cover"></div>
    </div>
  </div>

</template>	


<script>
export default {
  data() {
    return {
      nome: null,
      email: null,
      senha: null
    };
  },
  methods: {
    async cadastro() {
      try {
         await this.$auth.cadastroWith("local", {
          data: {
            nome: this.nome,
            email: this.email,
            senha: this.senha
          }
        });
 
        this.$router.post("/");
      } catch (e) {
        console.log(e);
      }
    }
  }
};
</script>


<style>
.cover {
  background: url("https://url.gratis/wftZc") center center;
}
</style>