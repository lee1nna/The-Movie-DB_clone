<template>
    <div>
        <Header/>
    </div>
</template>

<script>
import Header from '@/components/Header.vue'
import axios from 'axios'

axios.defaults.headers.common['api-key'] = '88c8e859d46625c472d014b2f3c995b0'

export default {
    components: {
        Header
    }
    
}
</script>