<template>
   <div>
      <h2>Witaj {{email}}</h2>
      <button @click="exit()">{{ buttonLabelToDisplay }}</button>
   </div>
</template>

<script>
export default {
 props: ['buttonLabel', 'authenticatedUsername'],
 data() {
     return {
         email: this.authenticatedUsername
     }
 },
 methods: {
     exit() {
         this.$emit('login', '');
     }
 },
 computed: {
     buttonLabelToDisplay() {
         return this.buttonLabel || 'Wyloguj się';  
     }
 }
}
</script>