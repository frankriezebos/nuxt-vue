<template> 
    <div>
        <TheNavbar/>
        <transition name="slideInFromBottom">
            <Nuxt />
        </transition>
    </div>
</template>

<script>
import TheNavbar from '@/components/TheNavbar'
export default {
    transition: {
        name: 'slideInFromBottom',
        mode: 'out-in'
    },
    components: {
        TheNavbar
    }
}
</script>
