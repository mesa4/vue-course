<template>
    <Introduction1 />
</template>

<script>
import { defineComponent } from 'vue';

import Introduction1 from './components/Introduction1.vue'

export default defineComponent({
    name: 'App',
    components: {
        Introduction1
    }
})
</script>
