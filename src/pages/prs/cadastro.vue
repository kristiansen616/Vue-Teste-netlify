<template>
  <div class="q-pa-md">
    <div class="q-card__section q-card__section--vert">
    <form  @submit.prevent.stop="onSubmit" @reset.prevent.stop="onReset">
     <div class="text-h6 doc-h6">Ficha de Cadastro</div>
      <br><hr>
        <div class="row">
        <div class="col-lg-12">
          <q-input
        ref="name"
        filled
        v-model="name"
        label="Digite seu Nome*"
        hint="Nome e sobrenome"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type something']"
        standout="bg-teal text-white"/>
        </div>
        </div>
        <br>
    <div class="row q-gutter-x-md">
      <div class="col-xs-12 col-sm-6 col-md-5">
        <q-input
        ref="age"
        filled
        type="number"
        v-model="Idade"
        label="Digite sua Idade*"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Please type your age',
          val => val > 0 && val < 100 || 'Please type a real age'
        ]"
      />
      </div>
    <div class="col-xs-12 col-sm-6 col-md-5">
       <q-input
        filled
        v-model="text"
        label="Digite sue e-mail*"
        hint="Não esqueça do @"
        lazy-rules
        standout="bg-teal text-white"/>
       </div>
      </div>
  <br>
    <div class="row">
        <div class="col-lg-12">
          <q-input
        ref="name"
        filled
        v-model="name"
        label="Digite o nome da Sua Mãe*"
        hint="Nome e Sobrenome"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type something']"
        standout="bg-teal text-white"/>
        </div>
        </div>
        <br>
    <div class="row q-gutter-x-md">
      <div class="col-xs-12 col-sm-6 col-md-5">
        <q-input
        filled
        v-model="number"
        label="Digite o número do seu celular*"
        hint="Somemte o número"
        lazy-rules
        standout="bg-teal text-white"/>
      </div>
    <div class="col-xs-12 col-sm-6 col-md-5">
       <q-input
        filled
        v-model="number"
        label="Digite o numero do seu Cpf*"
        hint="Somente o número"
        lazy-rules
        standout="bg-teal text-white"/>
       </div>
      </div>
      <br>
  <div>
        <q-btn label="Submit" type="submit" color="light-green-9" />
        <q-btn label="Reset" type="reset" color="light-green-9" flat class="q-ml-sm" />
      </div>
     </form>
    </div>
    </div>
</template>

<script>
export default {
  data () {
    return {
      name: null,
      age: null,

      accept: false
    }
  },

  methods: {
    onSubmit () {
      this.$refs.name.validate()
      this.$refs.age.validate()

      if (this.$refs.name.hasError || this.$refs.age.hasError) {
        this.formHasError = true
      } else if (this.accept !== true) {
        this.$q.notify({
          color: 'negative',
          message: 'You need to accept the license and terms first'
        })
      } else {
        this.$q.notify({
          icon: 'done',
          color: 'positive',
          message: 'Submitted'
        })
      }
    },

    onReset () {
      this.name = null
      this.age = null

      this.$refs.name.resetValidation()
      this.$refs.age.resetValidation()
    }
  }
}
</script>
