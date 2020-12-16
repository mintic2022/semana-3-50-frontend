<template>
  <div>
    
    
    <the-home />
  </div>
</template>

<script>
// @ is an alias to /src
import TheHome from '@/components/auth/TheHome.vue'
import TheLogin from '@/components/auth/TheLogin.vue'

export default {
  name: 'Home',
  components: {
    TheHome,
    TheLogin
    
    
    
  }
}
</script>
